import requests
import json

def emotion_detector(text_to_analyze):
    """
    Function to send text to Watson NLP Emotion Analysis service 
    and return the raw response.
    """
    # URL for the Watson NLP Emotion Predict service
    url = 'https://sn-watson-emotion.p.cloud.ibm.com/v1/watson.runtime.nlp.v1/NlpService/EmotionPredict'
    
    # Headers required by the API
    header = {"grpc-metadata-mm-model-id": "emotion_aggregated-workflow_lang_en_stock"}
    
    # Payload format for the Watson NLP service
    myobj = { "raw_document": { "text": text_to_analyze } }
    
    # Sending a POST request to the API
    response = requests.post(url, json=myobj, headers=header)
    
    # Returning the text attribute of the response
    return response.text
