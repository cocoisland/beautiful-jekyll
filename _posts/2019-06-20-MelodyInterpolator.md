---
title: Recurrent Neural Network generated Music
subtitle: Never heard before melodies created by three data scientists.
image: /img/melodyInterpolator/rockPiano.jpg
---
We built Melody Interpolator, a deep learning model using several LSTM layers to train on classical snippets and generate new melodies based on composers’ melodies. The purpose of the application is to investigate how well artificial intelligence generated music received by human listening experience. 


["Check out the live MelodyInterpolator"](https://melodyinterpolator.com "Live application running on Netlify") . Click on the upper left corner of the application for navigation.

![MelodyInterpolator Navigator](https://cocoisland.github.io/img/melodyInterpolator/appNavigator.png)

We have experimented with various LSTM (long short term memory) setting in our data model training. For classical music with frequent quick repeated notes, 512 LSTM hidden layer was found to learn keystroke too well resulting in too many repeated notes output. On general, training on 256 LSTM yielded better balance between repeated and varying notes rhythm. I also experimented modified the data model to training not only one attribute note, but also the velocity of the notes extracted from the raw midi input files. The training took days to training with GPU and sufficient memory. The resulted output songs was not ideal as it sounded a bit chaostic and seemed to lose its natural melody rhythm.

The project needed a frontend application to house all our generated songs. I volunteered to learn React programming on my own in two weeks and with guidance from my Project manager, we built the frontend application to display the generated song files which were hosted on Contentful website. Using API calls, Contentful website delivered the generated song files as json object to my React application which then extracted and displayed on UI-material cards objects. I then used ToneJS midi library to implement the play and stop functionalities, so that the React application become user-friendly to play music. As generated midi melodies sounded harsh if unrendered, we rendered to the generated midi melodies into mp3. Even though we are very much living in a digital world, our Human listening experiences are still more attune to smooth analog wave sound than harsh digital sound. Hence by converting digital song files to analog mp3 song files, greatly improved listening experience.

!["Library page"](https://cocoisland.github.io/img/melodyInterpolator/library.jpg)

The application backend was built by our team member who used AWS Elastic Beanstalk for hosting processed supported files. The backend gives users the option to select different flavor composer style song to be built. The raw output created will be in raw unrendered midi format.

!["Generator page"](https://cocoisland.github.io/img/melodyInterpolator/generator.jpg)

To learn the full working code, please visit [Melody Interpretter project on GitHub ](https://github.com/cocoisland/melodyInterpretter)
