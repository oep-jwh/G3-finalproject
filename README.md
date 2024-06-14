# 📙 Group 3 Final project 
+ Last updated (0610 by bori0824)
+ Presentation is scheduled on June 18 (Tuesday)
+ Overview of the project here :-)

## Useful Links
| 🔸[Emoji](https://gist.github.com/rxaviers/7360908) | 🔸[ProjectGuide](https://github.com/MK316/Spring2024/blob/main/DLTESOL/project/README.md) | 🔸[Reading material](https://raw.githubusercontent.com/MK316/Spring2024/main/DLTESOL/project/story03.txt) | 🔸[Coding] | 🔸 [APP#1](https://huggingface.co/spaces/joonp30/flashcard) | 🔸 [APP#2](https://bori0824-ImageUnscrambling.hf.space) | 🔸 [APP#3](https://huggingface.co/spaces/hannah416/during_comprehension_test) | 🔸 [APP#4](https://jinggujiwoo7-speechfeedback.hf.space) |🔸 [Visual Material#1] |🔸 [Visual Material#2](https://ai.invideo.io/watch/O5Q4fOeVnoH) |🔸 [Audio Material#1](https://bori0824-multitts.hf.space) |

## Lesson Plan

|             Grade            |     Proficiency Level (ACTFL)     |              Time Frame             |
|------------------------------|-----------------------------------|-------------------------------------|
|   Middle school 2<sup>nd </sup>grade    |         Intermediate-Low          |   50 mins.   (15 - 25 - 10 mins.)   |


|  Time |        Sequencing of Activities       |     Resources      |      Interactions     |
|-------|---------------------------------------|--------------------| ----------------------|
|   3   |       Icebreaking with the topic      | Visual Material #1 |        In class       |
|   7   |         Building Vocabulary           |        App #1      |        In pairs       |     
|   5   |    Guessing the story with images     |        App #2      |        In pairs       |  
|------ |---------------------------------------|--------------------| ----------------------|   
|   5   |   Introduced the story with a video   | Visual Material #2 | Individual - In pairs |
|  10   |   Understaning the story with audio   |  Audio Material #1 |        In class       |     
|  10   |    Checking Reading Comprehension     |        App #3      |       Individual      | 
|------ |---------------------------------------|--------------------| ----------------------|   
|  10   |    Thinking critically & Evaluating   |        App #4      | Individual - In class |     
|------ |---------------------------------------|--------------------| ----------------------| 

## Lesson Objectives 
+ To engage with Interactive Digital Content
+ To support to Collaborate and Communicate effectively
+ To strengthen Comprehension Skills
+ To develop Digital Proficiency
+ To experience a sustainable, paper-free learning environment
  
## Lesson Structure & Activities
### [Pre-reading activities (15 mins.)]
**👊 Icebreaking with the topic (3 mins.)**

**Activity:** Ss share their experiences and thoughts related to the topic introduced by T.
**App Functionality:**
**Objective:**

**🔤 Building Vocabulary (7 mins.)**

**Activity:** Students interact with an app to learn and practice key vocabulary related to the story through flashcards, matching games, or quizzes.
**App Functionality:** The app provides digital flashcards, interactive matching games, and quizzes that students can complete on their tablets.
**Objective:** Introduce and practice key vocabulary related to the story, enhancing students’ vocabulary knowledge.

# Install necessary libraries
!pip install gradio gtts Pillow requests

# Import libraries
import gradio as gr
from gtts import gTTS
from PIL import Image
import requests
from io import BytesIO

# Manually add definitions
word_definitions = {
    "quaint": "Having an old-fashioned or unusual quality or appearance that is usually attractive or appealing.",
    "explore": "To travel over or through (a place) in order to learn more about it or to find something.",
    "cheerful": "Feeling or showing happiness.",
    "peddler": "Someone who sells things in small amounts often by traveling to different places.",
    "curious": "Having a desire to learn or know more about something or someone.",
    "enthusiasm": "Strong excitement about something; a strong feeling of active interest in something that you like or enjoy.",
    "skeptical": "Having or expressing doubt about something.",
    "whisper": "To speak very softly or quietly."
}

# Corresponding image URLs (example URLs, replace with actual GitHub links)
image_urls = {
    "quaint": "https://raw.githubusercontent.com/PAMUS-JP30/flashcard/main/001.png",
    "explore": "https://raw.githubusercontent.com/PAMUS-JP30/flashcard/main/002.png",
    "cheerful": "https://raw.githubusercontent.com/PAMUS-JP30/flashcard/main/003.png",
    "peddler": "https://raw.githubusercontent.com/PAMUS-JP30/flashcard/main/004.png",
    "curious": "https://raw.githubusercontent.com/PAMUS-JP30/flashcard/main/005.png",
    "enthusiasm": "https://raw.githubusercontent.com/PAMUS-JP30/flashcard/main/006.png",
    "skeptical": "https://raw.githubusercontent.com/PAMUS-JP30/flashcard/main/007.png",
    "whisper": "https://raw.githubusercontent.com/PAMUS-JP30/flashcard/main/008.png"
}

def generate_output(word):
    definition = f"{word.capitalize()}: {word_definitions[word]}"
    
    # Get the image
    image_url = image_urls[word]
    response = requests.get(image_url)
    img = Image.open(BytesIO(response.content))
    img = img.resize((400, 250))  # Resize the image
    
    # Generate the audio
    tts = gTTS(text=definition, lang='en', tld='co.uk', slow=False)
    audio_file = f"{word}.mp3"
    tts.save(audio_file)
    
    return img, audio_file

# Create the Gradio interface
iface = gr.Interface(
    fn=generate_output,
    inputs=gr.Dropdown(choices=list(word_definitions.keys()), label="Choose a word"),
    outputs=[gr.Image(type="pil"), gr.Audio(type="filepath", autoplay=True)],
    title="Word Definition with Image and Audio"
)

# Launch the interface
iface.launch(share=True)




**🎰 Guessing the story wiwth images (5 mins.)**

**Activity:** Ss guess the story with the images related to the story. 
**App Functionality:** This application displays three WordCloud images meaning Intro, Body, and Conclusion and 6 random images of the story. Ss use their tablets to guess and discuss the story with peers and unscramble the random images in the right order after looking at the WordCloud imaages.
**Objective:** Encourage students to make predictions about the story and develop inferencing skills.



### [During-reading activities (25 mins.)]
**💻 Introduced the Story with a video (5 mins.)** 

**Activity:** Ss watch a teacher-created video of the full story, taking notes and paying attention to main characters, settings, and events.
**App Functionality:** The video is played on [the interactive whiteboard], and students can access the video on their tablets for closer viewing.
**Objective:** Provide an overview of the story and introduce the story through visual and auditory learning.

**🔈Understanding the Story with audio (10 mins.)**

**Activity:** Ss listen to the story in segments and answering the questions provided by T to enhance comprehension on the plot and main elements.
**App Functionality:** The app plays audio segments of the story [in class by T.] providing Ss with QR code to access on their tablets [when needed].
**Objective:** Focus on listening skills and detailed comprehension, identifying key story elements.

**📝 Checking Reading Comprehension (10 mins.)** 

**Activity:** Students answer multiple-choice, true/false, short answer, and vocabulary questions related to the story.
**App Functionality:** The app presents comprehension questions that students can answer on their tablets, providing immediate feedback.
**Objective:** Enhance Reading Comprehension skills and promote Critical Thinking and Vocabulary development.



### [Post-reading activity (10 mins.)]
**👄 [Thinking critically & Evaluating] (10 mins.)**

**Activity:** Ss receive common critical thinking questions instead of a reading passage and record their responses, listening to their pronunciation and evaluating it.
**App Functionality:** 
**Objective:** Develop Ss' ability to express personal opinions in English by responding to critical thinking questions.


## Lesson Materials

### Story Title: The Peddler's Magic Seeds 
+ [image link](https://github.com/MK316/Spring2024/blob/main/DLTESOL/project/Story03.png) 
+ [full-story text link](https://raw.githubusercontent.com/MK316/Spring2024/main/DLTESOL/project/story03.txt)
+ [full-story video link]( https://ai.invideo.io/watch/O5Q4fOeVnoH )

**<Synopsis>**
In a quaint village surrounded by rolling hills, young Tom struggled with the tough soil in his family's garden. One day, a peddler arrived selling various items, including magical seeds. Tom purchased a packet and planted them in his garden. To everyone's surprise, the seeds grew into vibrant and lush plants, transforming the barren garden into a wonder. The remarkable growth of these plants brought the community together, with neighbors sharing seeds and gardening tips. Inspired by the peddler, Tom later became a peddler himself, spreading joy and community spirit by selling magic seeds to other villages. Tom's story became a symbol of how small acts of kindness and curiosity can lead to widespread beauty and unity.
