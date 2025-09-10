# This code sample uses the 'requests' library:
# http://docs.python-requests.org
import requests
from requests.auth import HTTPBasicAuth
import json
import csv

def JiraBoard():
   url = "https://<You Atlas Domain>.atlassian.net/rest/api/3/search"

   auth = HTTPBasicAuth("<Email/Username of Your Jira Account>", "<Your Jira Token>")

   headers = {
      "Accept": "application/json"
   }

   query = {
      'jql': 'project = TTO'
   }

   response = requests.request(
      "GET",
      url,
      headers=headers,
      params=query,
      auth=auth
   )

   data = json.loads(response.text)
   selectedIssues=[]
   #Get all issues and put them into an array
   for issue in data['issues']:
      #print(issue)
      selectedIssues.append(issue)

   #Save data from Jira into a csv file
   with open('issues.csv', 'w', newline='') as csvfile:
      fieldnames = ['expand', 'key', 'id', 'fields', 'self']
      writer = csv.DictWriter(csvfile, fieldnames=fieldnames)
      for issue in selectedIssues:
         writer.writerow(issue)

JiraBoard()  
