## Welcome!

You can use the [editor on GitHub](https://github.com/Roway007/BeberAguaInLobe/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Este es mi proyecto es decir un modelo prototipo.


import base64
import requests

# Save string of image file path below
img_filepath = "path/to/image.jpg"

# Create base64 encoded string
with open(img_filepath, "rb") as f:
    image_string = base64.b64encode(f.read()).decode("utf-8")

# Get response from POST request
response = requests.post(
    url="http://localhost:38101/v1/predict/ef84b55d-4fca-4281-ada3-40041ce861f8",
    json={"image": image_string},
)
data = response.json()
top_prediction = data["predictions"][0]

# Print the top predicted label and its confidence
print("predicted label:\t{}\nconfidence:\t\t{}"
      .format(top_prediction["label"], top_prediction["confidence"]))
