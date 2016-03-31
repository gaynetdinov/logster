# Logster

An easy to parse, one line logger for Elixir Plug.Conn and Phoenix, heavily inspired by [lograge](https://github.com/roidrage/lograge).

With the default `Plug.Logger`, the log output for a request looks like this:
```
[info] GET /articles/some-article
[info] Sent 200 in 21ms
```

With Logster, we've got logging that's much more easily to parse and search through, such as:
```
[info] method=GET path=/articles/some-article format=html controller=HelloPhoenix.ArticleController action=show params={"id":"some-article"} status=200 duration=0.402 state=set
```

This becomes very handy specially when integrating with a log management service such as [Logentries](https://logentries.com/) or [Papertrail](https://papertrailapp.com/).

## Installation

First, add Logster to your `mix.exs` dependencies:

```elixir
def deps do
  [{:logster, "~> 0.1.0"}]
end
```

Then, update your dependencies:

```sh-session
$ mix deps.get
```

## Usage

To use with a Phoenix application, replace `Plug.Logger` in the `endpoint.ex` file with `Logster.Plugs.Logger`:

```elixir
# plug Plug.Logger
plug Logster.Plugs.Logger
```

To use it in as a plug, just add `plug Logster.Plugs.Logger` into your desired module

### License

The MIT License

Copyright (c) 2016-present Navin Peiris

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.