git---
layout: post
title: Soil Mate - Soil Texture App
subtitle: A soil texture helper app

---

The scope of the soil mate app is to collect soil data at sample locations in the field. The Soil Mate app is targeted across multiple industries, including agriculture, environmental science, geology and mining. Although focused on industry, the backyard gardener is encouraged to use it for personal gain as well!

### Ethos

In the modern online world, our data can be used without our knowledge for the gains of others. This is especially concerning for farmers, who’s farm data negatively impact their business options if they were made public or able to be bought. We believe that you, the user, should be in control of your data! This app allows you to collect soil texture data on your land while being in complete control of how that data is used and shared. 

*How do we ensure this?*

Firstly, the code of this app is open-source, meaning that others may check that we aren't collecting and sending your data anywhere it does not belong. Secondly, we don’t collect your data on a central server. Instead, you can export your data to wherever you like via means you have control over; such as email. 

### Principles

As the user selects a soil texture, they will realize each texture has a unique colour. The idea behind this stems from both the colour triangle and the soil texture triangle. Such that 100% sand is yellow, 100% silt is cyan, and 100% clay is magenta. By giving each texture class a percent sand silt and clay value which adds to 100, we can retrieve a unique colour for each class.

![colour triangle](https://i.pinimg.com/originals/44/35/aa/4435aa33a1a194344730eda010ae609d.png )
![texture triangle](https://www.qld.gov.au/__data/assets/image/0031/65758/soil-texture-large.jpg)

#### App Sample
![Gif of App](https://media1.tenor.com/images/11667551fe97716d986917dff6aef978/tenor.gif?itemid=19883454)


###  Features/Usage

Upon first use of the app the user will see an empty list and a bottom app bar. 

![Empty Sample List](https://i.imgur.com/P904mJc.jpeg)

The add button will take you to the add sample page where the user will have the option to choose a texture class, specify the depth range, and add a custom sample ID.

![Add sample page](https://i.imgur.com/UVmTsiQ.jpeg)

Once ‘Submit’ is pressed, a new card will appear on the main sample list page (see gif). The information contained in the card includes:
 * ID (Automatically incremented by one for each subsequent sample)
 * Name of texture class
 * A general estimate of the percentage of sand silt and clay
 * The depth range
 * The location

![Sample List](https://i.imgur.com/aO17edP.jpeg)


Finally, after the user has populated the sample list, they have the option to “Export Data”, which will create a csv file that the user will be prompted to share on external applications such as email. To start from the beginning the “Delete All” feature will empty the sample list.

### Upcoming Features

#### Site list

Future app features will include a site list. This breaks samples into groups based on sites, for instance, “Back Paddock”. 

#### Manage sites and samples

The user will have the option to manage sites and samples, which includes editing and deleting individual samples or sites.

#### Map

A map this the sample location pins. The pins will be colour coded depending on the texture type. 

### Get Involved

The current version of the app is close to publishing on the app stores. Get involved and suggest future improvements of the app on our [GitHub](https://github.com/Open-Source-Agriculture/soil_mate/issues) by submitting a “New Issue”.

Alternatively, join the discussion on [Discord](https://discord.gg/8x58DuxfGz) or follow us on [LinkedIn](https://www.linkedin.com/company/open-source-agriculture).

Written by Hephzibah Crossing
