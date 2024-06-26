# DatoCMS GraphQL Client

# Initialization

In config/config.exs:

```elixir
config :my_app,
  api_key: System.get_env("DATOCMS_API_KEY")
```

```elixir
datocms_api_key = Application.fetch_env!(:my_app, :api_key)
DatoCMS.GraphQLClient.configure(api_key: datocms_api_key)
```

# Environments
If you've multiple DatoCMS environment you can control which one we'll fetch data from by using the :environment keyword.
Example:
```elixir
datocms_api_key = Application.fetch_env!(:my_app, :api_key)
DatoCMS.GraphQLClient.configure(api_key: datocms_api_key, environment: "stage")
```

# Queries

* single items: `DatoCMS.GraphQLClient.fetch!(:foo, "{ bar }").bar`,
* localized single items: `DatoCMS.GraphQLClient.fetch_localized!(:foo, :en, "{ bar }")`,
* collections: `DatoCMS.GraphQLClient.fetch_all!(:allFoos, "{ bar }")`,
* localized collections: `DatoCMS.GraphQLClient.fetch_all_localized!(:allFoos, :en, "{ bar }")`.

# Structured Text

DatoCMS structured text fields are complex, and rendering them
as HTML is hard.

This library provides the helper `DatoCMS.StructuredText.to_html/2`,
which takes the structured text part of a GraphQL response and
transforms it into HTML.

This repo contains a Livebook, 'structured_text.livemd' which
walks through how to handle the various types of rendering.
