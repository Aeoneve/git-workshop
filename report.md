HW 2, CS 625, Fall 2021
================
Andrew Pale
Sep 9, 2021

# Part 1

## Data Cleaning Steps

Analyzed the “kind of pet” column

-   Created a text facet
-   Manually examined the data
-   Excluded obvious joke data
    -   Car
    -   Card Board Poster
    -   Katze
    -   Robot
    -   Roomba
    -   Server
    -   Virus
    -   Blank
-   Split multi-valued cells on the following
    -   Dog, dog, dog, cat
-   Cluster and edited the data
    -   Used key collision and fingerprint to combine the following
        -   Dog, dog, Dog., dog :))))) to Dog
        -   Cat, cat, Cat!, Ca to Cat
        -   Guinea pig, Guinea Pig to Guinea Pig
        -   Bunny, bunny to Rabbit
        -   Hamster, hamster to Hamster
        -   Hermit Crab, Hermit crab to Hermit Crab
    -   Used key collision and metaphone3 to combine the following
        -   Dog, dig, Doggo to Dog
        -   Beta fish, Betta fish to Fish
    -   Used key collision and Daitch-Mokotoff to combine the following
        -   Phoebe, Puppy to Dog
    -   Used key collision and Beider-Morse to combine the following
        -   Cat, Cats to Cat
    -   Used nearest neighbor and levenshtein with radius 15 and block
        chars 3 to combine the following
        -   Chinchilla, Chinchilla (Other) to Chinchilla
        -   Fish, Goldfish, Indoor goldfish to Fish
        -   Kitten, Kitty Meow to Cat
        -   Spider, Spiney leaf insect to Insect
        -   Snake, Other: snake to Snake
        -   Lizard, Leopard Gecko to Lizard
-   Manually edited the following which weren’t picked up in the
    aforementioned steps
    -   God, dlg, Luna, Mona, Pit Bull, Sog, (blank) to Dog
    -   Compared a number of “Other” animals to their breed to obtain a
        “kind” of animal

Analyzed the “pet’s age” column

-   Created a numeric facet
-   Isolated the Non-numeric data
    -   Obtained all the values that specified years with the following
        GREL code and trasnformed them into numbers
        -   toNumber(value.replace(" years“,”"))
    -   Obtained all the values that specified months with the following
        GREL code and trasnformed them into numbers
        -   toNumber(value.replace(" months“,”")) / 12.0
    -   Obtained all the values that specified weeks with the following
        GREL code and trasnformed them into numbers
        -   toNumber(value.replace(" months“,”")) / 52.14
    -   Removed data where pets were deceased
        -   -   if(or(or(value.contains(/.*(Deceased).*/),
                value.contains(/.*(deceased).*/)),
                or(value.contains(/.*(Dead).*/),
                value.contains(/.*(dead).*/)), "", value)
    -   Manually edited a number of ages to convert them to numbers
        -   This included ages that weren’t picked up in the
            aforementioned steps because they included odd text or other
            values
    -   Split two entries up, one containing three dogs and another
        containing three dogs and one cat
        -   This was done by splitting the pets by name and then
            duplicating the other information manually

Analyzed the “pet’s breed” column

-   Cluster and edited the data
    -   Used key collision and fingerprint to combine the following
        -   Variations of Golden Retriever, Domestic Shorthair, Domestic
            Longhair, Lab Mix, Golden Doodle, Cavalier King Charles
            Spaniel, West Highland White Terrier, Shih Tzu, Basset
            Hound, Bernese Mountain Dog, Cocker Spaniel, Border Collie,
            Whippet, Persian, Havanese, German Shepherd, Yellow Labrador
            Retriever, English Springer Spaniel, Rhodesian Ridgeback,
            Tuxedo Cat, Guinea Pig, Russian Dwarf Hamster, Siamese,
            Cockapoo, Maine Coon, West Highland Terrier, Australian
            Shepherd, Rottweiler, American Shorthair, Australian Cattle
            Dog, Corgi, Chihuahua, Pitbull, Maltipoo, Pembroke Welsh
            Corgi, Mini Schnauzer, Terrier, Beagle, Springer Spaniel,
            Miniature Dachshund, Dachshund, Russian Blue, Chocolate
            Labrador Retriever, English Cocker Spaniel, Jack Russell
            Terrier, Black Labrador Retriever, Miniature Schnauzer,
            British Shorthair, German Shepherd, Tortoise Shell, Toy
            Poodle, Pug, YorkiePoo, Poodle, Border Collie, Siberian
            Husky, King Charles and mixed were combined together
    -   Used key collision and metaphone3 to combine the following
        -   Variations of American Shorthair, Blue Tick Coon Hound,
            Domestic Shorthair, Shih Tzu, Long-haired Chihuahua,
            Goldendoodle, Tortoise Shell, Pitbull, Maine Coon, and mixed
            were combined together
    -   Used key collision and metaphone3 to combine the following
        -   Variations of German Shepherd, Domestic Shorthair, Golden
            Retriever, Yorkshire Terrier, Treeing Walker Coonhound,
            Australian Shepherd, Black Labrador Retriever, Jack Russell
            Terrier, Blue Tick Coon Hound, Blue Tick Coon Hound, Basset
            Hound, Cairn Terrier, American Pitbull, Yorkiepoo, French
            Bulldog, Miniature Schnauzer Bichon Frise, Chocolate
            Labrador Retriever, Weimaraner, and Mixed were combined
            together
    -   Used key collision and cologne-phonetic to combine the following
        -   Variations of Shih Tzu and Mixed were combined
    -   Used key collision and Daitch-Mokotoff to combine the following
        -   Variations of Border Collie, West Highland White Terrier,
            Dachshund, Labradoodle, Chocolate Labrador Retriever,
            Newfoundland, Foxhound, Catahoula, Mini Dachshund, Golden
            Retriever, Great Pyrenees, Boston Terrier, Bichon Frise,
            Cairn Terrier, Yorkshire Terrier, King Charles, Tortoise
            Shell, Yellow Labrador Retriever, Russian Dwarf Hamster,
            Winter White, and Mixed were combined together
    -   Used nearest neighbor and levenshtein with radius 3 and block
        chars 3 to combine the following
        -   Shorthair Calico, Terrier, Pointer, Greyhound, Maltese,
            American Shorthair, Chihuahua, Cairn Terrier, Poodle, Boston
            Terrier, Dalmatian, Blue Heeler, Mixed were combined
            together
-   Transformed the data with a GREL expression to check for any breeds
    that mention the words “Mix” or “mix” and change the entire entry to
    “Mixed”. Additionally, a second expression was used to check for “/”
    or “" and change the entry entry to”Mixed" if found
    -   if(or(value.contains(/.*(Mix).*/), value.contains(/.*(mix).*/)),
        “Mixed”, value)
    -   if(or(value.contains(/.*(/).*/), value.contains(/.*(\\).*/)),
        “Mixed”, value)
-   Split an entry up containing two cats
    -   This was done by splitting the pets by name and then duplicating
        the other information manually
-   Created a text facet
-   Manually examined the data
-   Combined breeds not caught by previous methods

# Part 2

## How many types (kinds) of pets are there?

**There are 24 different types of pets not including the two “Other”
pets of indeterminate species**

![Data](Kind_of_pet.png)

## How many dogs?

**There are a total of 1135 dogs**

## How many breeds of dogs?

**There are a total of 118 dog breeds including “Mixed” and “(blank)”**

![Data](Dog_breeds.png)

## What’s the most popular dog breed?

**Not including “Mixed”, which accounted for 253 dogs, the Golden
Retriever was the most popular breed with 185 dogs**

## What’s the age range of the dogs?

**The youngest is months old and the oldest is 22 years**

## What’s the age range of the guinea pigs?

**From 1 year to 5 years**

![Data](Guinea_age.png)

## What is the oldest pet?

**The oldest pet is Bruce Springsteen, a cat, at 24 years**

![Data](Pet_age.png)

## Which are more popular, betta fish or goldfish? How many of each?

**Betta fish are more popular with 14. There are a total of 9
goldfish.**

![Data](Fish_data.png)

## What’s the most popular everyday name for a cat?

**The most popular everyday name for cats is “Kitty”**

![Data](Cat_name.png)

## What’s the most popular full name for a dog?

**The most popular full name for a dog is tied between the names
“Maggie” and “Sadie”, both with a count of 7. However, if including last
names, “Sadie” wins out slightly as “Sadie Blue”, “Sadie Jo”, and “Sadie
Mae” bringing the count to 10. There are only two other dogs with the
name “Maggie” - “Maggie Peaches” and “Maggie Pie Thatcher”**

![Data](Dog_name.png)

## References

-   <https://github.com/jgolbeck/petnames>
