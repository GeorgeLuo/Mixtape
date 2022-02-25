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
--web-media content that comes for youtube, vimeo, etc. Dimensions are
    offset - the time from beginning to seek
    duration - the time from offset or beginning to consume
--local-media a local file. Same dimensions as web-media.
```

## Business Logic
