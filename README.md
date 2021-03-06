Configuration for the `@interrupt` bot in [cloudfoundry.slack.com](https://slack.cloudfoundry.org/).

 * running with [dpb587/slack-delegate-bot](https://github.com/dpb587/slack-delegate-bot)
 * deployed on [Pivotal Web Services](https://run.pivotal.io/)

To change behavior, add or update your team in the [`config` directory](./config), run the [`validate`](./validate) script, and then send a pull request with your improvements.

If you are using Pair.ist with a non-public team:

 * configure the `password` field as `$PAIRIST_TEAM_{NAME}`
 * share the password with `dberger` so he can add it as an environment variable for the bot

---

    fly -t "$FLY_TARGET" set-pipeline \
      --pipeline cloudfoundry-slack-interrupt-bot \
      --config ~/workspace/src/github.com/dpb587/slack-delegate-bot/examples/cf-app/concourse.yml \
      --load-vars-from <( lpass show --notes "github.com/dpb587/cloudfoundry-slack-interrupt-bot//vars.yml" )
