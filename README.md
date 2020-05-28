# ArchiMob corpus Preprocessing for Mozilla DeepSpeech

 <p> The importer pre-processes the audio-and text-data so that it can be used with the open-source Speech-to-Text engine DeepSpeech. This repository is forked from *tobiasrordorf/archimob-swissgerman-deepspeech-importer*. Please reach out to <a href='https://www.linkedin.com/in/tobiasrordorf'>Tobias Rordorf</a> for specifics.

**I have edited ReadMe and a few files so it can directly be used for <a href='https://github.com/AASHISHAG/deepspeech-swiss-german'>deepspeech-swiss-german</a> repository.**  </p>

**Table of Contents**

- [How to access](#How_to_access)
- [ArchiMob Corpus](#ArchiMob_Corpus)
- [Pre-processing Steps](#Pre-processing_Steps)

## How to access
<p> You need to contact <a href='https://github.com/AASHISHAG/deepspeech-swiss-german'>Dr. Samardžić</a> for the access. More details can be referred at <a href='https://www.spur.uzh.ch/en/departments/research/textgroup/ArchiMob.html'>The ArchiMob Corpus</a>
  
## ArchiMob Corpus
<p> The ArchiMob corpus represents German linguistic varieties spoken within the territory of Switzerland. This corpus is the first electronic resource containing long samples of transcribed text in Swiss German, intended for studying the spatial distribution of morphosyntactic features and for natural language processing. </p>

This corpus is available under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License.

**Size: ~70 hours**

## Pre-processing Steps

- If you have acquired the audio files as mentioned above, create a folder called 'audio' and place the files in this folder. 

1. Audio files are merged from subfolders into one folder in './Pre_Processing_Files/audio_merged'.
2. Wav-Files are pre-processed according to above format-specifications and stored in './Pre_Processing_Files/audio_processed_final'
3. The CH and DE words are extracted from the XML-files and joined to strings with the corresponding media-pointer ID (which matches the audio_filename), and stored in csv per XML-file
4. Duplicates and zero values in transcriptions  are removed. (List of removed duplicates are available in './Pre_Processing_Files/CSV_Merged/')
5. All csv per language are merged
6. A csv that contains [wav_filename], [wav_filesize] of all wav files in './Pre_Processing_Files/audio_processed_final/' is created.
7. The transcriptions, filenames and filesizes are merged and files below 10'000 Bytes and above 318'400 Bytes are dropped. (See comment below)
8. The merged transcripts are then cleaned of unwanted characters (e.g. semicolon, commas etc.)
9. The DE-transcriptions of files of the package 'd1163' are removed because they have not been translated

The final transcripts are splitted into train (75%), dev (15%) and test (10%) files and stored in ./Final_Training_CSV_for_Deepspeech/'



