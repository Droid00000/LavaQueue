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

Gets a track from the queue at the specified index. Response is a [track](https://lavalink.dev/api/rest#track) object.

```
GET /v4/sessions/{sessionId}/players/{guildId}/queue/tracks/{index}
```

## Get Next Track

Gets next track in the queue. Response is a [track](https://lavalink.dev/api/rest#track) object.

```
GET /v4/sessions/{sessionId}/players/{guildId}/queue/next
```

## Get Previous Track

Gets the previously playing track. Response is a [track](https://lavalink.dev/api/rest#track) object.

```
GET /v4/sessions/{sessionId}/players/{guildId}/queue
```

### Get Queue History

Gets the history of this queue. Response is an array of [track](https://lavalink.dev/api/rest#track) objects.

```
GET /v4/sessions/{sessionId}/players/{guildId}/history
```

### Get Queue History Track

Gets a track from the history at the specified index. Response is a [track](https://lavalink.dev/api/rest#track) object.

```
GET /v4/sessions/{sessionId}/players/{guildId}/history/{index}
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

Adds a track at the specified index. Reuqest body is an [update player track](https://lavalink.dev/api/rest#update-player-track).

```
PUT /v4/sessions/{sessionId}/players/{guildId}/queue/tracks/{index}
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

> [!CAUTION]
> This route will override any existing tracks in the queue.

```
PUT /v4/sessions/{sessionId}/players/{guildId}/queue/tracks
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

> [!CAUTION]
> This does not remove the track at the original index.

```
POST /v4/sessions/{sessionId}/players/{guildId}/queue/{index}/move?position=0
```

Response:

```
```

### Delete Queue

```
DELETE /v4/sessions/{sessionId}/players/{guildId}/tracks/queue
```

### Delete Queue Track(s)

> [!NOTE]
> If amount is provided, the specified number of elements after the index will be removed.

```
DELETE /v4/sessions/{sessionId}/players/{guildId}/queue/{index}?amount=0
```