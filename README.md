# LavaQueue

> [!IMPORTANT]
> This plugin is compatible with Lavalink version four and higher.

A plugin that adds a queue system for [Lavalink](https://github.com/lavalink-devs/Lavalink).

## Summary

* [Installation](#installation)
* [Lavalink Usage](#lavalink-usage)

## Installation

To install this plugin either download the latest release and place it into your `plugins` folder or add the following into your `application.yml`

Replace x.y.z with the latest version number or short commit hash.

```yaml
lavalink:
  plugins:
    - dependency: "com.github.topi314.lavaqueue:lavaqueue-plugin:x.y.z"
      snapshot: false # set to true if you want to use snapshot builds (currently required)
```

## Lavalink Usage

### Queue Types:

* `normal`
* `repeat`
* `track`

### Get Queue

```
GET /v4/sessions/{sessionId}/players/{guildId}/queue
```

Response:

```
```

### Get Queue Track

```
GET /v4/sessions/{sessionId}/players/{guildId}/queue/tracks/{index}
```

Response:

```
```

## Get Next Track

```
GET /v4/sessions/{sessionId}/players/{guildId}/queue/next
```

Response:

```
```

## Get Previous Track

```
GET /v4/sessions/{sessionId}/players/{guildId}/queue
```

Response:

```
```

### Get Queue History

```
GET /v4/sessions/{sessionId}/players/{guildId}/history
```

Response:

```
```

### Get Queue History Track

```
GET /v4/sessions/{sessionId}/players/{guildId}/history/{index}
```

Response:

```
```

### Update Queue

> [!IMPORTANT]
> This route will override any existing tracks in the queue.

```
PATCH /v4/sessions/{sessionId}/players/{playerId}/queue
```

Request:

```json5
{
  "type": "normal",
  "tracks": [
    {
      "encoded":"QAAAjQIAJVJpY2sgQXN0bGV5IC0gTmV2ZXIgR29ubmEgR2l2ZSBZb3UgVXAADlJpY2tBc3RsZXlWRVZPAAAAAAADPCAAC2RRd"
    }
  ]
}
```

Response:

```
```

### Add Queue Track

```
POST /v4/sessions/{sessionId}/players/{guildId}/queue/tracks/{index}
```

Response:

```
```

### Add Queue Tracks

```
POST /v4/sessions/{sessionId}/players/{guildId}/queue/tracks
```

Request:

```json5
{
  [
    {
      "encoded": "QAAAjQIAJVJpY2sgQXN0bGV5IC0gTmV2ZXIgR29ubmEgR2l2ZSBZb3UgVXAADlJpY2tBc3RsZXlWRVZPAAAAAAADPCAAC2RRd"
    }
  ]
}
```

Response:

```
```

### Update Queue Tracks

> [!IMPORTANT]
> This route will override any existing tracks in the queue.

```
PATCH /v4/sessions/{sessionId}/players/{guildId}/queue/tracks
```

Request:

```json5
{
  [
    {
      "encoded": "QAAAjQIAJVJpY2sgQXN0bGV5IC0gTmV2ZXIgR29ubmEgR2l2ZSBZb3UgVXAADlJpY2tBc3RsZXlWRVZPAAAAAAADPCAAC2RRd"
    }
  ]
}
```

Response:

```
```

### Move Queue Track

> [!IMPORTANT]
> This does not remove the track at the original index.

```
POST /v4/sessions/{sessionId}/players/{guildId}/queue/{index}/move?position=
```

Response:

```
```

### Delete Queue

```
DELETE /v4/sessions/{sessionId}/players/{guildId}/tracks/queue
```

### Delete Queue Track(s)

If amount is provided, n number of elements after the index will be removed.

```
DELETE /v4/sessions/{sessionId}/players/{guildId}/queue/{index}?amount=0
```