# OPINION-MINING

**Read Me 
**
Our system is a Sarcasm Detector which takes text input, gives the user ability to check if the sarcasm exists in the text. There are 3 models BAAI,MINILM,BERT. 

Our project has 2 part the front end and the back end. The front end is done with anvil which is a online web building and hosting website that runs on python. It was build mostly on the website so there is no exact front end for say in code, there some code that connect backend with the front end.But it had to be on the website to run it: 

**The code is: 
**

from ._anvil_designer import Form1Template 
from anvil import * 
import anvil.server 
import anvil.tables as tables 
import anvil.tables.query as q 
import anvil.js  
import webbrowser  
from anvil.tables import app_tables 
 
 
 
class Form1(Form1Template): 
def __init__(self, **properties): 
# Set Form properties and Data Bindings. 
self.init_components(**properties) 
self.setup() 
 
def setup(self): 
self.detect_model1.set_event_handler('click',self.detect_click_model_1) 
self.detect_model2.set_event_handler('click',self.detect_click_model_2) 
self.detect_model3.set_event_handler('click',self.detect_click_model_3)  
 
# Any code you write here will run before the form opens. 
def detect_click_model_1(self,**event_args): 
"""This method is called when the button is clicked""" 
detect_sarcasm_1= anvil.server.call('detect_sar_1',self.input.text) 
if detect_sarcasm_1: 
self.result.visible=True 
self.result.text="The text is "+ detect_sarcasm_1 
def detect_click_model_2(self,**event_args): 
"""This method is called when the button is clicked""" 
detect_sarcasm_2= anvil.server.call('detect_sar_2',self.input.text) 
if detect_sarcasm_2: 
self.result_2.visible=True 
self.result_2.text="The text is "+ detect_sarcasm_2 
def detect_click_model_3(self,**event_args): 
"""This method is called when the button is clicked""" 
detect_sarcasm_3= anvil.server.call('detect_sar_3',self.input.text) 
if detect_sarcasm_3: 
self.result_3.visible=True 
self.result_3.text="The text is "+ detect_sarcasm_3 
 
 
 
 
This configures the various button to get input form google collab. 
This code in Google collab will connect it(Its already there but just letting you know the connection form frontend and backend: There a server key that my website generates, which collab uses to connect. 

!pip install anvil-uplink 
import anvil.server 
 
anvil.server.connect("server_GZMJ3FGREXONNV7RQ3PFQ6DI-BX4UIUOEXNLMKCT7") 
 
// setup training and prediction code here 
 
 
@anvil.server.callable 
def detect_sar_3(input): 
query = 'eating in a tall building helps grow taller' 
sarcasm_text= input 
result = predict_sarcasm(sarcasm_text) 
 
return sarcasm_text +" : " + result +" from BAAI " 
// here you can see detect_sar_3, which is a function we told the website to look out for so as soon as this returns a value the website picks it up and displays it.This is how the front end and back end works 

 
The front end link: https://nutty-kind-enthusiasm.anvil.app/ 

The website should be online anytime you visit it, the models however rely on google Collab to run so they could have timed out when you get to running it. 

Here are link to Google collab: Check Github 


We have 3 models available, which can be run independently to check for sarcasm. Training and running each model take around 6 min to 1 hors 30 min  to run. We recommend using T4 GPU. You can pick the model you want to run choose a gpu and select run all, you will get a message after the second step asking to restart the session, just close it and the rest should run without hiccups. One you see the last cell running of the collabs go to the frontend website, put in a sarcasm comment and it should detect it. 
You can run all 3 Collab simultaneously and click all the buttons, it will work as well. 

**Running steps: 
**
Open the google Collab 
Download all  files form Integrated_code 
Upload to google collab,
Run all 3 of them, 
Ignore the restart message, 
Verify last cell is running, It a while loop that keeps Collab on so that we can communicate with anvil without connection lost. 

Then go the website(we had no choice with the link name it was auto generated) 
https://nutty-kind-enthusiasm.anvil.app/ 
then put a sarcastic or non sarcastic text in the input area, and click on the model you want to run and you should see the result just below where you entered. 
  
 ** Known Bugs: 
**If it seems that no matter what you type you get the same result, switch to another cpu / gpu train it and you should be able to get valid result. 


We focused more on BAAI and it is the most accurate almost the 3 model 
 

**#NOTE TO GRADER 
**If any reason the token expires or the website is not up or you need help with setting up, 
Please email any of us, we are using free versions of website so they may have expired,  Krishnc1@umbc.edu, 
 


