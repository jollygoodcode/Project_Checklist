Project Checklist

```
### Communication

- [ ] Chronicles.io
- [ ] PivotalTracker
- [ ] GitHub (with empty repo and copy Project Checklist to Issues)
- [ ] Slack and Integrations

### App Development

- [ ] Heroku (Staging)
- [ ] Heroku (Production)
- [ ] Codeship
- [ ] deppbot

### Slack Integrations

- [ ] Chronicles.io
- [ ] PivotalTracker
- [ ] GitHub
- [ ] Heroku
- [ ] Codeship

### Optionals

- [ ] CodeClimate
- [ ] HoundCI

## Pre-Production

As we start to build the project, we need to check the following:

### Code
- [ ] Latest version of Ruby and Rails defined in Gemfile
- [ ] Ensure all configuration and keys are stored in ENV variables
- [ ] Ensure all Model associations have the necessary `dependent: destroy`
- [ ] Setup [Attache](github.com/choonkeat/attache) + AWS S3 for storing user-generated content

### Optimization

- [ ] Optimize according to suggestions by [Google's Pagespeed](https://developers.google.com/speed/pagespeed/insights/)
  - Use `heroku-deflater` - see [blog](http://jollygoodcode.github.io/2015/10/20/rails-response-and-assets-compression-on-heroku.html)
- [ ] Enable `bullet` and `lol_dba` and check and optmize all SQL queries
- [ ] Optimize all images with [ImageOptim](https://github.com/toy/image_optim) or [Smusher](https://github.com/grosser/smusher)
- [ ] Enable lazy loading of images if app is image heavy

### ActiveJob

- [ ] Ensure all/most emails are sent via background processes
- [ ] Ensure all/most images are processed via background processes, or use [Attache](https://github.com/choonkeat/attache)

### Optional
- [ ] Ensure Web Accessibility with [WAVE](https://chrome.google.com/webstore/detail/wave-evaluation-tool/jbbplnpkjmmeebjpijfedlgcdilocofh?hl=en-US)

Production
- [ ] Concurrent Server
  - Puma recommended at 1-2 x `PUMA_WORKER`
- [ ] Start your Worker?
- [ ] Setup Database with (sizable) Memory
  - Postgres DB on Standard 0 ([Migrate from Dev DB](https://devcenter.heroku.com/articles/upgrading-heroku-postgres-databases))
  - Set Connection Pool
- [ ] Setup Backup Strategy
  - `heroku pg:backups schedule --at '03:00 Asia/Singapore' DATABASE_URL --app <app>`
- [ ] Setup Logging Strategy
  - [logentries](https://elements.heroku.com/addons/logentries) - `heroku addons:add logentries`
- Setup Monitoring
  - [ ] [Skylight.io](https://www.skylight.io/)
  - [ ] [New Relic](https://elements.heroku.com/addons/newrelic) - `heroku addons:add newrelic && heroku config:add NEW_RELIC_APP_NAME=<app>`
  - [ ] [UptimeRobot](https://uptimerobot.com/)
  - [ ] [Notable](https://github.com/ankane/notable)
- [ ] Setup Errors Tracking
  - [RuntimeError.net](https://elements.heroku.com/addons/runtimeerror)  
  - [Party Foul](https://github.com/dockyard/party_foul)
  - [logster](https://github.com/discourse/logster)
- [ ] Update DNS
  - Add custom domains (www and root) to Heroku
  - CNAME `www` to Heroku URL; Redirect 302 `root` to `www`
- [ ] Update DNS Entry for Mail Services
  - [Sendgrid](https://sendgrid.com/docs/Glossary/spf.html)
  - [Mandrill](http://help.mandrill.com/entries/22030056-How-do-I-add-DNS-records-for-my-sending-domains-)
- [ ] Update Basement specific ENV in Heroku's config (e.g. WWW_HOSTNAME etc)
```
