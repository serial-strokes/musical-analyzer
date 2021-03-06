# Musical Analyzer | Serial Strokes

## Dependencies

- Ruby (to run the tests)
- Docker

## Test and build

To execute docker build, docker tests and python tests:

    bundle install --binstubs --path vendor/bundle
    bundle exec rspec --format doc

To execute docker build only:

    docker build --rm --tag serial-strokes/musical-analyzer:latest .

To execute python tests only (they depends on docker build):

    docker run -it --entrypoint="" --rm serial-strokes/musical-analyzer:latest pytest -rA

## Run

    docker run \
        -it \
        --rm \
        --volume serial-strokes-library-volume:/opt/library:ro \
        serial-strokes/musical-analyzer:latest \
        beat_tracker /usr/local/lib/python3.8/site-packages/librosa/util/example_data/Kevin_MacLeod_-_Vibe_Ace.ogg
