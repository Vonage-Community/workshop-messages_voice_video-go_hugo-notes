---
title: "Webhooks"
weight: 2
---

## Rooms URL

Room related events are sent to the **Rooms URL**:

```json
"{\"event\":\"room:expired\",\"room_id\":\"c55b592c-d5cc-4525-b714-86d2c1a4aa65\",\"room_type\":\"instant\",\"expires_at\":\"2022-10-09T21:24:01.194Z\",\"created_at\":\"2022-10-09T21:14:01.195Z\"}"
```

## Sessions URL

Participants related events are sent to the **Sessions URL**:

```json
"{\"event\":\"session:started\",\"session_id\":\"1_MX40NjMzOTg5Mn5-MTY2NTM1NDkyMjEyM35KWDV1NWpRUE43aDE0cTd6QjIvb2V1Znh-fg\",\"room_id\":\"5c4ef488-ed5a-48ac-93e0-44b1d4de5428\",\"started_at\":\"2022-10-09T22:35:22.225Z\"}"
```

```json
"{\"event\":\"session:participant:joined\",\"participant_id\":\"11c0313a-f78f-4aad-82b7-b1ff99013ef1\",\"session_id\":\"1_MX40NjMzOTg5Mn5-MTY2NTM1NDkyMjEyM35KWDV1NWpRUE43aDE0cTd6QjIvb2V1Znh-fg\",\"room_id\":\"5c4ef488-ed5a-48ac-93e0-44b1d4de5428\",\"name\":\"Paul Ardeleanu\",\"is_host\":true}"
```
...

```json
"{\"event\":\"session:participant:left\",\"participant_id\":\"11c0313a-f78f-4aad-82b7-b1ff99013ef1\",\"session_id\":\"1_MX40NjMzOTg5Mn5-MTY2NTM1NDkyMjEyM35KWDV1NWpRUE43aDE0cTd6QjIvb2V1Znh-fg\",\"room_id\":\"5c4ef488-ed5a-48ac-93e0-44b1d4de5428\",\"name\":\"Paul Ardeleanu\",\"is_host\":true}"
```

```json
"{\"event\":\"session:ended\",\"session_id\":\"1_MX40NjMzOTg5Mn5-MTY2NTM1NDkyMjEyM35KWDV1NWpRUE43aDE0cTd6QjIvb2V1Znh-fg\",\"room_id\":\"5c4ef488-ed5a-48ac-93e0-44b1d4de5428\",\"started_at\":\"2022-10-09T22:35:22.225Z\",\"ended_at\":\"2022-10-09T22:36:08.916Z\"}"
```
