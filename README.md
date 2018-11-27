# matrix-puppet-slack

This is an unofficial matrix slack bridge that works by means of [user puppetting](https://github.com/AndrewJDR/matrix-puppet-bridge).

Get your `user_access_token` from here:

https://api.slack.com/docs/oauth-test-tokens

The bridge uses that access token to connect as a client using the slack RTM API.

This technique does not require admin on the slack team; instead, the bridge is simply a custom slack client.

The bridge supports multiple teams at once, see the config.sample.json

## installation

clone this repo

cd into the directory

run `npm install`

## configure

Copy `config.sample.json` to `config.json` and update it to match your setup. Add as many teams as you like by adding them to the array.

## register the app service

Generate an `slack-registration.yaml` file with `node index.js -r -u "http://your-bridge-server:8090"`

Note: The 'registration' setting in the config.json needs to set to the path of this file. By default, it already is.

Copy this `slack-registration.yaml` file to your home server. Make sure that from the perspective of the homeserver, the url is correctly pointing to your bridge server. e.g. `url: 'http://your-bridge-server.example.org:8090'` and is reachable.

Edit your homeserver.yaml file and update the `app_service_config_files` with the path to the `slack-registration.yaml` file.

Launch the bridge with ```node index.js```.

Restart your HS.

## Features and Roadmap

 - [x] Multi-team
 - [x] Channel messages
 - [x] Direct messages
  - [x] Recieving
  - [ ] Initiating
 - Matrix -> Slack
   - [x] Text content
   - [x] Formatted Text content
   - [ ] Image content
   - [ ] Audio (m.audio msgtype events)
   - [ ] Video content (m.video msgtype events)
   - [x] Generic file uploads (m.file msgtype events)
   - [ ] Typing notifs
   - [ ] User Profiles
 - Slack -> Matrix
   - [x] Text content
   - [x] Formatted Text content
   - [x] Image/Audio/Video content as protected link to slack
   - [x] Image/Audio/Video content as upload & embed to matrix
   - [x] Image/Audio/Video content message text
   - [x] Typing notifs
   - [ ] User Profiles
   - [ ] Presence
 - [x] Third Party Lookup
  - [x] Rooms
  - [x] Users
 - [x] Puppet a user's real Slack account.
 - [ ] Rooms react to Slack updates
