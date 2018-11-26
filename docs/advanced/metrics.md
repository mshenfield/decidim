# Metrics

Metrics calculations must be executed everyday. Some `rake task` have been added to perform it.

- To execute all metrics at once. Related to previous date from *today*

  ```ruby
  bundle exec rake decidim:metrics:all
  ```

- To execute an specific metric. Related to previous date from *today*

  ```ruby
  bundle exec rake decidim:metrics:one["<metric name>"]
  ```

- To execute metrics for a given date (all or an specific one)

  ```ruby
  bundle exec rake decidim:metrics:all["YYYY-MM-DD"]
  bundle exec rake decidim:metrics:one["<metric name>","YYYY-MM-DD"]
  ```

## Current available metric names

- *users*, confirmed `Users`
- *proposals*, available `Proposals`
- *accepted_proposals*, currently accepted `Proposals`
- *votes*, votes in `Proposals`
- *assemblies*, public `Assemblies`
- *participatory_processes*, public `ParticipatoryProcesses`
- *results*, `Resultsp` in `Accountabilities`
- *comment*, `Comments` generated by users, related to public elements and not *hidden*
- *meetings*, public `Meetings`

Only available for `ParticipatorySpaces` (restricted to `ParticipatoryProcesses`)

- *participants*: unique users who make at least one of the following actions
  - Create a proposal
  - Create a debate
  - Answer a survey
  - Leave a comment
  - Give support to a proposal
  - Endorse
  - Vote a participatory budgeting project
- *followers*: unique users who follow any participatory element in a `ParticipatorySpace`
- *endorsements*: number of `Endorsements` in `Proposals`, within a `ParticipatorySpace`
- *debates*: number of `Debates` within a `ParticipatorySpace`
- *survey_answers*: number of answered `Surveys` by users within a `ParticipatorySpace`

## To configure it correctly

- A **crontab** line must be added to your server to maintain them updated daily. You could use [Whenever](https://github.com/javan/whenever) to manage it directly from the APP
- A **ActiveJob** queue, like [Sidekiq](https://github.com/mperham/sidekiq) or [DelayedJob](https://github.com/collectiveidea/delayed_job/)