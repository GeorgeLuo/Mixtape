# Mixtape
a cli for music collection playback management

## Usage
Mixtape-cli is a tool used to create & manage sets of audio tracks. Effectively, the output is a playlist with precision in terms of segmentation, playback speed control, transitions, etc.

The content pool supported will derive from your local files, or the universe of audio within youtube videos. The underlying scraping mechanism is a fork of youtube-dl, therefore the library of content available should match whatever youtube-dl can find.

```
mixtape-cli [tags]
```

### Tags

Generally order will not matter when appending arguments and options. 

Common sense UX is exercised with regards to repeat options (multiple values) and appearance of options.

Multi-value.

```
mixtape-cli --web-media https://www.youtube.com/watch?v=fffffffffff --web-media https://www.youtube.com/watch?v=ffffffffffa
```

Generally values with more dimensions will be delimited with a semi-colon by key-value.

```
mixtape-cli --local-media file=/Users/user/Documents/some_sound.wav;offset=5s;duration=10s
```

Notice time will be expressed as above, or ie 1m28s359ms.

The defined tags are

```
--web-track content that comes for youtube, vimeo, etc. Dimensions are
    offset - the time from beginning to seek
    duration - the time from offset or beginning to consume
--local-track a local file. Same dimensions as web-media.
--def-file provide a definition file
```

### Mixtape definition file

A json formatted mixtape definition can be provided to the cli, defining the features and attributes as the tags do. Tags will apply on top of definition files (logically as if file is converted to tags and tags then applied).

```
mixtape-cli --def-file mt1_definition.json
```
```
{
    "tracks": [
        {
            "source": "https://www.youtube.com/watch?v=fffffffffff",
            "duration": "1m3s",
            "offset": "15s",
            "source_type": "web"
        },
        {
            "source": "/Users/user/Documents/some_sound.wav",
            "source_type": "local"
        }
    ]
}
```

The mix defined above takes the contents of media found at ```https://www.youtube.com/watch?v=fffffffffff``` from time 0:15 to time +1m3s, or 1:18 and appends after it the entirety of ```/Users/user/Documents/some_sound.wav```.

## Business Logic
