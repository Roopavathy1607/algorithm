from googleapiclient.discovery import build
def submit_url_for_indexing(url, type): 
indexing = build('indexing', 'v3')
request = {
'url': url,
'type': type
}
response = indexing.urlNotifications().publish(url=url,
body=request).execute() if 
response['status']['code'] == 200: print('URL 
submitted for indexing successfully.')
else: print('Error submitting URL for indexing:', 
response['status'])
def get_indexing_status(url): 
indexing = build('indexing', 'v3')
response = 
indexing.urlNotifications().get(url=url).execute() if 
response['status']['code'] == 200:
print('Indexing status:', response['urlNotification'])
else: print('Error retrieving indexing status:', 
response['status'])