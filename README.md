# ![](https://github.com/project-red-siren-dsi-chi-cc7/wip) Project Red Siren

---

## Creators

[Lance Carroll](https://www.linkedin.com/in/lance-carroll/)  
[Neal Manahan](https://www.linkedin.com/in/neal-manahan/)  
[Rodolfo Flores Méndez](https://www.linkedin.com/in/rodolfo-flores-mendez/)  
[Sardorkhon Tursunov](https://www.linkedin.com/in/sardorkhont/)  
[Blake Wallace](https://www.linkedin.com/in/blake-wallace)  

---

## Problem Statement


**Problem 10: Using live police radio reports for real time identification of people needing assistance.**

*Problem Statement:* Currently, FEMA identifies areas that require immediate attention (for search and rescue efforts) either by responding to reports and requests put directly by the public or, recently, using social media posts. This tool will utilize live police radio reports to identify hot spots representing locations of people who need immediate attention. The tool will flag neighborhoods or specific streets where the police and first-respondents were called to provide assistance related to the event.

#### Questions of Interest to this project
Is it possible to train a model to predict an emergency with a 95% or better accuracy?  
Can any meaningful data related to addresses be gotten from live audio feed?

---

## Contents
[Dictionary](#dictionary)  
[Executive Summary](#executive-summary)  
[Future iterations/next steps](#next-steps)  
[Known Issues](#known-issues)  
[Data Sources](#data-sources)  
[Sources](#sources)

---

<a id='data-dictionary'></a>

## Data Dictionary

<p align="left"> 
    
|Feature (Bin #)|Description|
|---|---|
file_name|Name of .wav Audio File
class|Emergency or Non-Emergency
emergency_type|Description of Situation
origin|Broadcastify or YouTube
good_exception|Whether or not Speech Detection API detected audio or not
audio_recognition|Speech-to-Text of the Audio Clip
tempogram_#|Tempo
spectral_contrast_#|Spectral Contrast
chroma_cens_#|Chroma Feature Normalized
spectral_centroid|Spectral Centroid
spectral_band|Spectral Bandwidth
spectral_flat|Spectral Flatness
rolloff|Spectral Rolloff
chroma_cqt_#|Chroma Continuous Q Transform
tonnetz_#|Tonnetz
contrast_#|Spectral Contrast
mel_#|Mel Scale
chroma_stft_#|Chroma Short Time Fourier Transform
mfcc_#|Mel Frequency Cepstrum
preds|Model Prediction of Class

</p>

---

<a id='executive-summary'></a>

## Executive Summary

*“To know even one life has breathed easier because you have lived. This is to have succeeded.” – Ralph Waldo Emerson  
"Prepared. Responsive. Committed." - FEMA Motto*


August 29, 2005, Hurrican Katrina slams into the shores of the United States, leaving a wake of devastation.  To compound the issue, poorly constructed levees along the shores of Louisiana are overpowered, and entire sections of the city of New Orleans are left submerged under water.  As rain falls and water levels rise, people everywhere find themselves in dire situations, trapped in buildings, on rooftops, and ultimately stuck in ways they cannot evade.  Sadly, hundreds of people loose there lives.  

During this tragic event, emergency responders were left with the task of attending to would be victims, while simultaneously struggling to find those who needed assistance.  Project Red Siren successfully lays the foundation needed to expand the resources available to FEMA when attempting to find people needing immediate assistance.  It specifically addresses the question, is this radio chatter from first responders and dispatchers an emergency?  While this question is not deep enough on its own to answer the full problem statement, the model produced is quite accurate, making it a solid starting point for further investigations.

To be precise, the model uses various properties of sound waves to isolate tones, inflections, and other parts of speech that become more pronounced when people are put under stress or duress.  Yes, they are emergency responders and dispatchers, trained to keep their composure in tough situations.  This fact is one of the most remarkable things about the model Project Red Siren has produced.   The differences, although subtle, are nevertheless present; and the precision of the computer classified emergencies with 98% accuaracy on new data. 

This accuracy was from the beginning amazing to us.  It is a great foundation for further work toward a more robust system that will assist FEMA in determining relevant locations from policy scanner radio broadcasts.  

---

<a id='known-issues'></a>

## Known Issues

During Project Red Siren, several challenges were revealed, which are significant in future considerations.  First, and most pronounced, the model is not now producing any address information.  There are two big hurdles in this domain, that of the inconsistencies involved with how addresses are communicated, and also the ability to obtain clear enough streaming audio to get meaningful text extraction.  In the former, a small amount of work was done.  Ultimately, this is where the most significant amount of work still exists in getting a model completely to production.  Future iterations/next steps should focus heavily in this area.  Project Red Siren can say that there is a great source already in existence, [Google Cloud's speech-to-text](https://cloud.google.com/speech-to-text/?utm_source=google&utm_medium=cpc&utm_campaign=na-US-all-en-dr-bkws-all-all-trial-b-dr-1006141&utm_content=text-ad-none-any-DEV_c-CRE_113193385807-ADGP_Hybrid+%7C+AW+SEM+%7C+SKWS+%7C+US+%7C+en+%7C+BMM+~+Speech+API-KWID_43700009979724579-kwd-141369776212&utm_term=KW_%2Bcloud%20%2Bspeech-ST_%2Bcloud+%2Bspeech&gclid=CjwKCAjwtYXmBRAOEiwAYsyl3BrJXG-Nw448eS7nRbqbMMM1s5FBhT7WgNCzbdbDye2Qd_OHCTfwohoCZ68QAvD_BwE).  But, their domain API is not available without a cost, which was outside of the realm of the resources available for Project Red Siren.  

Another noteworthly challenge, there are many features which [LibRosa](https://librosa.github.io/librosa/index.html), the primary tool used to create visuals from the sound, can take measurements on and return.  These can get a bit technical.  Please see [EDA_and_modeling](https://github.com/project-red-siren-dsi-chi-cc7/deliverables/blob/master/EDA_and_modeling.ipynb#Audio-features) for a more thorough consideration of the LiBrosa features.

---

<a id='next-steps'></a>

## Future iterations/next steps

Pushing Project Red Siren further, as mentioned above, there is a desperate need for work in the realm of speech to text.  We refer to the [Proof of concept](https://github.com/project-red-siren-dsi-chi-cc7/deliverables/blob/master/Proof%20of%20concept.ipynb) notebook, which outlines in more detail a potential large scale workflow useful in tackling the main problem.  

A few highlights of this proposed workflow, it incorporates criterion to address the question, how much text data should the machine store when receiving text from live audio?  It also incorporates deep learning into its scope, and briefly mentions the importance of periodic updating of the model to maintain training data on newly acquired incoming data.

---

<a id='data-sources'></a>

## Data Sources

 [Broadcastify](http://www.broadcastify.com/)  
 [You Tube](https://www.youtube.com/)  
- [Baltimore Police Dispatch Scanner Audio Shooting suspect arrested after wild high-speed chase](https://www.youtube.com/watch?v=fw8i4wQRoM8&t=62s)
- [Baltimore Police radio the night of the Freddie Gray riots, 9 PM to midnight, April 25, 2015](https://www.youtube.com/watch?v=5GwW7N73Hqo)
- [Chicago Fire - Digital Dispatch Scanner Audio 2-11 fire and EMS Plan 3 kills 10 kids](https://www.youtube.com/watch?v=7bf2sPR7Gqo&t=111s)
- [Chicago Police Chase with Scanner Audio](https://www.youtube.com/watch?v=rznw_VMnXnE&t=112s)
- [Chicago Police Dispatch Scanner Audio Police officers injured in crash while chasing stolen BMW](https://www.youtube.com/watch?v=a5SGC2N4QLU)
- [Chicago Police Zone 11 Dispatch Scanner Audio Shots fired at and by the police 10-1](https://www.youtube.com/watch?v=Ftw3AxiMl2w&t=61s)
- [Chicago Police Zone 12 Dispatch Scanner Audio Chicago Police Officer shot 10-1](https://www.youtube.com/watch?v=8IQ3bYUylns&t=46s)
- [Dayton Police and Fire Dispatch Scanner Audio Fatal crash on I-75 with tanker truck](https://www.youtube.com/watch?v=5MQqEv9eZ2Y)
- [FDNY Bronx Dispatch Scanner Audio Deadly 5th alarm fire in the Bronx kills over 10](https://www.youtube.com/watch?v=lZvHmfBskEw&t=3s)
- [FDNY Queens Dispatch Scanner Audio 5 killed including 2 Children in 3rd Alarm fire](https://www.youtube.com/watch?v=pJ5rPStdj7U&t=56s)
- [G20 Pittsburgh: Scanner recordings of "police riot" at University of Pittsburgh](https://www.youtube.com/watch?v=W-cxHC_JU8o)
- [Illinois State Police Dispatch Scanner Audio High speed chase of suspect wanted for killing deputy](https://www.youtube.com/watch?v=cpcz2FXOZgE&t=512s)
- [NJ State Police Troop B Dispatch Scanner Audio Deadly School Bus crash Interstate 80](https://www.youtube.com/watch?v=SrQFDzD3YyA)
- [NYPD Citywide 1 Radio Comms during Ferguson Protest](https://www.youtube.com/watch?v=GJQ9g-koF_U)
- [Philadelphia Police - Citywide Dispatch Scanner Audio Philadelphia Eagles win Super Bowl 52](https://www.youtube.com/watch?v=Aih-9ZpvfAk)
- [Philadelphia riots: Eagles fans celebrate Super Bowl win with fire, destruction, mayhem](https://www.youtube.com/watch?v=wZS4gNVvW7o)
- [Scanner Audio From the Charlotte-Mecklenburg Police Riot - 9-20-16](https://www.youtube.com/watch?v=jeHUJz_xU3w)
- [St. Louis City Fire Dispatch Scanner Audio 5-alarm fire at south St. Louis warehouse](https://www.youtube.com/watch?v=uCDbon7-Yxo&t=57s)
- [2,000 Kids Riot, Shutdown Kentucky Mall (POLICE SCANNER AUDIO)](https://www.youtube.com/watch?v=tMObeEXl8r0)

---

<a id='sources'></a>

## Sources

 - [Audio Spectrum Explained](https://www.teachmeaudio.com/mixing/techniques/audio-spectrum/)
 - [Banse, Rainer and Klaus R. Scherer. “Acoustic profiles in vocal emotion expression.” Journal of personality and social psychology 70 3 (1996): 614-36 .](https://pdfs.semanticscholar.org/94ef/3dcacea9c1d1a032d7d724bd4b09cae13f7f.pdf)  
 - [LibROSA](https://librosa.github.io/librosa/index.html)  
 - [Tian, M., Fazekas, G., Black, D. and Sandler, M. (2019). On the use of the tempogram to describe audio content and its application to Music structural segmentation - IEEE Conference Publication. [online] Ieeexplore.ieee.org. Available at: https://ieeexplore.ieee.org/document/7178003 [Accessed 24 Apr. 2019].](http://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7178003&isnumber=7177909)
 - Wikipedia contributors, "Mel-frequency cepstrum," Wikipedia, The Free Encyclopedia, https://en.wikipedia.org/w/index.php?title=Mel-frequency_cepstrum&oldid=886751555 (accessed April 24, 2019).
 - Wikipedia contributors, "Mel scale," Wikipedia, The Free Encyclopedia, https://en.wikipedia.org/w/index.php?title=Mel_scale&oldid=889156041 (accessed April 24, 2019).
 - Wikipedia contributors, "Chroma feature," Wikipedia, The Free Encyclopedia, https://en.wikipedia.org/w/index.php?title=Chroma_feature&oldid=884367502 (accessed April 24, 2019).
 - Wikipedia contributors, "Spectrogram," Wikipedia, The Free Encyclopedia, https://en.wikipedia.org/w/index.php?title=Spectrogram&oldid=893824963 (accessed April 24, 2019).