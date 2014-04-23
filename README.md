# Introduction

![Suave Logo](https://raw.githubusercontent.com/SuaveIO/suave/master/media/suave1.png)

Suave is a simple web development F# library providing a lightweight web server
and a set of combinators to manipulate route flow and task composition. Suave
is inspired in the simplicity of Happstack and born out of the necessity of
embedding web server capabilities in my own applications.  Still in its early
stages Suave supports HTTPS, multiple TCP/IP bindings, Basic Access
Authentication, Keep-Alive. Suave also takes advantage of F# asynchronous
workflows to perform non-blocking IO. In fact, Suave is written in a completely
non-blocking fashion throughout.

What follows is a tutorial on how to create applications. Scroll past the
tutorial to see detailed function documentation.

# Tutorial: Hello World!

The simplest Suave application is a simple HTTP server that greets all visitors
with the string `"Hello World!"`

``` fsharp
open Suave // always open suave
open Suave.Http.Successful // for OK-result
open Suave.Web // for config
web_server default_config (OK "Hello World!")
```

Now that you've discovered how to do "Hello World!", go read the
[rest of the documentation](http://suave.io/)

# Coding Guidelines

Suave.X where X is a module is where we expect users to look. We don't expect users
of the library to have to look at Y in Suave.X.Y, so for server-specific code, please
stick to the Y module/namespace. That way we make the API discoverable.

We have a [TeamCity CI server](https://tc-oss.intelliplan.net/overview.html) set
up to provide continuous integration for Suave. You can pull nugets from this
server, by adding
https://tc-oss.intelliplan.net/guestAuth/app/nuget/v1/FeedService.svc/
to your list of nuget sources; this allows you to get pre-release nugets of
suave directly into your development environment.

## Style Guide

Two space indentation.

``` fsharp
match x with // '|' characters at base of 'match'
| A     -> ()
| Bcdef -> "aligned arrows" // space after '|' character
```

Parameters

Let type annotations be specified with spaces after the argument symbol and before
the type.

``` fsharp
static member FromString(scheme : string, ?cert) =
```

Method formatting with no spaces after/before normal parenthesis

``` fsharp
let my_method_name first_arg (second : WithType) = async { // and monad builder
  return! f first_arg second
  } // at base of 'let' + 2 spaces
```

You need to document your methods with '///' to create XML-doc. A XML
documentation file is generated together with the compilation and is distributed
with the NuGet so that others can read your code's intentions easily.

Don't put unnecessary parenthesis unless it makes the code more clear.

## Testing

Run Tests as a console app. Return status code = 0 means success.

# Community

## Chat Room

We have a chat room in case you feel like chatting a bit. 

[![Chat Room](https://badges.gitter.im/SuaveIO/suave.png)](https://gitter.im/SuaveIO/suave)

## Integrations

 * https://github.com/rayokota/generator-angular-suave