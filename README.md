# Image Classifier

### Known Architectural Limitation — Synchronous Model Training

Currently, model training executes synchronously within the HTTP request/response cycle. In a production environment this would cause requests to time out for any reasonably sized dataset. The solution is to decouple training from the web layer by queuing training jobs with Celery and a message broker such as Redis, allowing training to run asynchronously as a background task. This would also require a polling or WebSocket mechanism to notify the user when training completes.

### Key Features

* Lifecycle management:

      * Quickly create machine learning models with the use of templates
      * Save/delete and retrain models              


* Adjustable training parameters:

      * Learning rate
      * Minimum accuracy
      * Number of epochs


* Performance Metrics:

      * Training v Validation accuracy/loss grpahs
      * Key Performace Indicators
          Precision
          Recall
          F1 Score
          Training time

* Automatic label generation:
  

  __NB__ _When uploading training/validation dataset for binary classification. Please structure your zip file as follows._
  
  Example:   _cats-v-dogs.zip_

    
      cats_or_dogs
        |
        +- cats
        .  |
        .  +- cat.0.jpg
        .     .
        .     .
        .     .
        .    cat.999.jpg
        .    
        +- dogs
           |
           +- dog.0.jpg
              .
              .
              .
              dog.999.jpg
  
* User management

  _TODO_


___


## Docker


### Build and tag a Docker image
```bash
docker build -t <your_tag_name>/image_classifier .
```

### Start Docker container
```bash
docker run -p 8000:8000 --name <your_container_name> <your_tag_name>/image_classifier
```
