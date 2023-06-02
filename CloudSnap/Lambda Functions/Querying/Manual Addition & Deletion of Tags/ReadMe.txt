# Manual Addition or Removal of Image Tags

This function enables users to manually add or remove tags of an image via an API. This is made possible by submitting a POST request containing a JSON message with the desired modifications.

## How It Works

1. **API Call:** Users can send a POST request to the API endpoint. This request should include a JSON message detailing the changes to be made.

2. **JSON Message:** The JSON message sent should follow the format:

    ```json
    {
      "url":"https://cloudsnap.s3.amazonaws.com/image1.png",
      "type": 1, /* 1 for add and 0 for remove */
      "tags": [
        {
          "tag": "person",
          "count": 2
        },
        {
          "tag": "alex",
          "count": 1
        }
      ]
    }
    ```
    Here, the "type" field indicates the operation, with 1 for adding a tag and 0 for removing a tag. The "tags" field is an array of objects, each containing a "tag" and "count" field.

3. **Tag Modification:** Based on the "type" field, the system will add or remove the specified tags from the image. If "type" is set to 0, the system will remove the tags up to the maximum of either the available tags or the count value.

4. **Lambda Function:** The process of adding or removing tags involves triggering a Lambda function that updates the entry in the database.

## Usage

To use this service, you need to send a POST request with the JSON message as described above. The system will then modify the tags of the specified image according to your instructions.


## Notes

- If "count" is not specified in the request, the default value of 1 will be used.
- If a tag is not included in the list of tags requested for deletion, the request will simply ignore it.
