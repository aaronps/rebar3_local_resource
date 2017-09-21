# rebar3_local_resource

A rebar plugin to use local directory as resource, usefull for example to
create plugins and using it without git or other weird method.

## Use

Add the plugin to your rebar config, and use `{local, "path/to/directory"}` as
resource:

    {plugins, [
        { rebar3_local_resource, {git, "https://github.com/aaronps/rebar3_local_resource.git", {branch, "master"}} },
        { some_local_plugin, {local, "path/to/some_local_plugin"} }
    ]}.

If you modify your local resource (for example, plugins) and want to upgrade it
just tell rebar3 todo, this plugins always upgrades the resource without any
check, in theory you should know if update is needed and tell rebar what to do.

## History

I needed some way to develop rebar3 plugins and thought about this. After some
searching on how to use `rebar_file_utils:cp_r/2` for making this plugin, I
found that the own rebar3 tests has `rebar_localfs_resource` which is almost
what I needed.

Some modifications and tests later this is the result.