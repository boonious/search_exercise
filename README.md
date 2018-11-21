# IR [![Build Status](https://travis-ci.org/boonious/information_retrieval.svg?branch=master)](https://travis-ci.org/boonious/information_retrieval) [![Coverage Status](https://coveralls.io/repos/github/boonious/information_retrieval/badge.svg?branch=master)](https://coveralls.io/github/boonious/information_retrieval?branch=master)

IR is an [Elixir-based](https://elixir-lang.org) exercise in information retrieval, in-memory indexing and full-text searching.

### Usage - Interactive Elixir (IEx)

The application can be invoked interactively through
[IEx](https://elixir-lang.org/getting-started/introduction.html#interactive-mode).


```bash
  # from application home directory,
  # start IEx with the application running
  # this will also compile the application if it hasn't been compiled
  ...$ iex -S mix
    
  # or start IEx with shell history
  ..$ iex --erl "-kernel shell_history enabled" -S mix
  
```

```elixir
  # build an in-memory corpus for the entire dataset
  iex> {:ok, corpus} = IR.parse(:all)

  # corpus of specific number of documents
  iex> {:ok, corpus} = IR.parse(2)

  # build an in-memory index for the entire dataset
  iex> {:ok, index} = IR.indexing(:all)
  
  # index specific number of documents
  iex> {:ok, index} = IR.indexing(500)
  ... # %{ "term" => "postings"..}

  # indexing and build text corpus
  iex> {:ok, index, corpus} = IR.indexing(5000, corpus: true)
  ...

  # more instructions forthcoming
```

## CSV data

A dataset can be supplied in a CSV file named `data.csv`, in the application
home directory. It currently imports `title` and `description` columns
which should be specified with such headers in the file.
Existing data from other columns will not be parsed.

The default dataset filename and path can be configured in
`config/config.exs`:

```elixir
  config :ir,
    data_filepath: "another_path/another_filename.csv"
```

## Requirement
This application is based on [Erlang](http://erlang.org/doc/installation_guide/INSTALL.html).
To compile and build the application, [Elixir](https://elixir-lang.org) is required.
You can install Elixir on OS X via Homebrew with:

```bash
  brew install elixir
```

The above installs both Elixr and Erlang.
For other OSes, check the [installation instructions](http://elixir-lang.org/install.html) on elixir-lang.org.

To compile the application, run the following from the application home directory:

```elixir
  ...$ mix deps.get; mix compile
```

## Documentation

API documentation can be generated with the following command:

```bash
  ...$ mix docs
  Docs successfully generated.
  View them at "doc/index.html".
```



