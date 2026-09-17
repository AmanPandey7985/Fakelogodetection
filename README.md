Fake Logo Detection

Fake Logo Detection is a web based logo verification system that
analyzes an uploaded logo and compares it with a collection of existing
logos. The system uses deep learning based image features and cosine
similarity to identify visually similar logos.

The application is designed to help determine whether an uploaded logo
closely matches an existing logo in the database. Based on the
similarity score, the application presents the result as an original
logo, a new logo, or a logo that may require further investigation.

Project Overview

The project consists of a React frontend and a Flask backend.

The frontend allows a user to upload a logo image through a simple drag
and drop interface. The image is sent to the Flask backend, where it is
stored and processed.

The backend uses the VGG16 model without its final classification layers
to extract visual features from the uploaded image. These features are
compared with stored feature vectors using cosine similarity. The system
then returns the most similar logos along with their similarity scores.

The application displays the uploaded image, the classification result,
and the logos that have the highest similarity to the submitted image.

Key Features

Logo image upload through the web interface

Image processing and feature extraction using VGG16

Comparison of image features using cosine similarity

Retrieval of the most similar logos from the available database

Similarity scores for retrieved logos

Classification based on the highest similarity result

Image storage using MongoDB GridFS

Responsive React based user interface

How the System Works

A user uploads a PNG, JPG, or JPEG logo through the frontend.

The React application sends the uploaded image to the Flask backend.

The backend stores the uploaded image using MongoDB GridFS.

The uploaded image is resized to 224 by 224 pixels and processed using
the preprocessing method required by VGG16.

VGG16 extracts the visual feature representation of the image.

The extracted feature vector is compared with the stored logo feature
vectors using cosine similarity.

The system identifies the top matching logos.

The similarity result is returned to the frontend.

The frontend displays the classification and the most similar logos with
their similarity percentages.

Classification Logic

The application uses the similarity of the highest matching result to
determine how the uploaded logo is presented.

A very high similarity result is presented as an original logo.

A low similarity result is presented as a new logo.

A similarity result between these ranges is presented as likely
plagiarized and may require further investigation.

These classifications are based on the similarity thresholds implemented
in the application and should not be treated as a legal determination of
trademark ownership or infringement.

Technology Stack

Frontend

React

Vite

React Router

HTML

CSS

Backend

Python

Flask

Flask CORS

Machine Learning and Image Processing

TensorFlow

VGG16

Pillow

NumPy

Pandas

Scikit learn

Database

MongoDB

MongoDB GridFS

Deployment

Firebase Hosting configuration is included in the project.

Project Structure

fake-logo-detection

backend

app.py

src

RIS.py

combine.ipynb

public

src

Components

assets

App.jsx

Home.jsx

Query.jsx

main.jsx

package.json

package-lock.json

vite.config.js

firebase.json

index.html

Requirements

Node.js and npm are required for the React frontend.

Python is required for the Flask backend.

MongoDB is required for storing uploaded images through GridFS.

The machine learning environment requires TensorFlow, Pillow, NumPy,
Pandas, and Scikit learn.

Running the Frontend

Open a terminal in the project directory and install the frontend
dependencies.

npm install

Start the development server.

npm run dev

The Vite development server will provide the local address for the
frontend.

Running the Backend

Open a terminal in the backend directory.

Create and activate a Python virtual environment.

Install the Python dependencies required by the backend and machine
learning code.

Start the Flask application.

python app.py

The current frontend configuration sends image requests to the Flask
server running on localhost port 5000.

Machine Learning Approach

The project uses VGG16 as a pretrained convolutional neural network for
extracting image features.

The final classification layers of VGG16 are not used. Instead, the
convolutional feature representation is flattened into a feature vector.

Cosine similarity is then calculated between the uploaded logo feature
vector and the stored feature vectors. The results are sorted to
identify the most similar logos.

This approach allows the system to compare the visual characteristics of
logos rather than relying only on their filenames or textual
information.

Data

The project uses precomputed image feature vectors and annotation files
for the logo comparison process.

Large feature vector and dataset files are not intended to be stored
directly in the Git repository. They should be provided separately when
setting up the complete local environment.

Testing Scope

This project was developed and tested using a limited set of logos rather than a large-scale production dataset. The current results should therefore be considered a demonstration of the approach and not a benchmark of real-world classification performance.

Limitations

The result represents visual similarity and does not establish legal
ownership or trademark infringement.

The quality of the result depends on the quality and coverage of the
logo database.

The current implementation relies on locally available feature vectors
and a local MongoDB instance.

The frontend currently uses a local Flask backend URL for API requests,
so additional configuration is required before deploying the complete
application with a publicly accessible backend.

Future Improvements

The system can be extended with a larger and more diverse logo database.

The similarity model can be evaluated and tuned using a dedicated
validation dataset.

The backend can be deployed as a public API instead of relying on a
local server.

Environment variables can be introduced for database and API
configuration.

Authentication and access control can be added for production use.

A more formal evaluation framework can be introduced to measure
classification accuracy, precision, recall, and other relevant metrics.

Author

Aman Pandey

Project Purpose

This project was developed as an application of deep learning, image
processing, and similarity search to a practical logo verification
problem.
