# Phoenix Template Engine for Markdown

> Powered by [Earmark](https://github.com/pragdave/earmark)


## Usage

  1. Add `{:phoenix_markdown, "~> 0.1.0"}` to your deps in `mix.exs`.
  2. Add the following to your Phoenix `config/config.exs`

     ```elixir
    config :phoenix, :template_engines,
      md: PhoenixMarkdown.Engine
     ```

    If you are also using the [phoenix_haml](https://github.com/chrismccord/phoenix_haml) engine, then it should look like this:
     ```elixir
    config :phoenix, :template_engines,
      haml: PhoenixHaml.Engine,
      md:   PhoenixMarkdown.Engine
     ```


  3. Use the `.html.md` extensions for your templates.

## Optional

Add md extension to Phoenix live reload in `config/dev.exs`

```elixir
  config :hello_phoenix, HelloPhoenix.Endpoint,
    live_reload: [
      patterns: [
        ~r{priv/static/.*(js|css|png|jpeg|jpg|gif|svg)$},
        ~r{web/views/.*(ex)$},
        ~r{web/templates/.*(eex|md)$}
      ]
    ]
```

If you are also using the [phoenix_haml](https://github.com/chrismccord/phoenix_haml) engine, then the pattern should look like this:

```elixir
  config :hello_phoenix, HelloPhoenix.Endpoint,
    live_reload: [
      patterns: [
        ~r{priv/static/.*(js|css|png|jpeg|jpg|gif|svg)$},
        ~r{web/views/.*(ex)$},
        ~r{web/templates/.*(eex|haml|md)$}
      ]
    ]
```

## Generators / Use

There are no generators for phoenix_markdown since they wouldn't make sense.

Markdown is intended to be written by a human in any text editor or in a fancy one like [iA Writer](https://ia.net/writer). Just create a file with the .md extension and drop it into the appropriate templates folder in your phoenix application. Then you can use it just like any other template.

## Elixir 1.3 note

I'll take a dependency on Earmark 0.2.2 as soon as it ships on hex. That will clean up the numerous build warnings under Elixir 1.3

In the mean time, if you want to get rid of those warnings now, you can override the dependency by specifying the master version of Earmark in your mix.exs file like this.

```elixir
  {:earmark, git: "https://github.com/pragdave/earmark.git", override: true},
```
