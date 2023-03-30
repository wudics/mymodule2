# mymodule2
It is a amxmodx template for ambuild. You can use ambuild to build this on Linux or Windows.

# how to use

## download the right position

in your `amxmodx/modules/` direcotry, use below git command to clone mymodule.

```bash
git clone https://github.com/wudics/mymodule2.git czfun
```

`czfun` whitch is named with your module name.

## rename the module

and then, use your text editor (like vscode) to open `AMBuilder` file.

find below content:

```python
binary = AMXX.MetaModule(builder, 'mymodule2')
```

and change `mymodule2` to `czfun`, like below:

```python
binary = AMXX.MetaModule(builder, 'czfun')
```

## add to ambuild compile task

edit `amxmodx/AMBuildScript` file with your text editor.

find the content like:

```python
builder.RunBuildScripts(
  [
    'amxmodx/AMBuilder',
    'compiler/amxxpc/AMBuilder',
    'compiler/libpc300/AMBuilder',
    'modules/cstrike/cstrike/AMBuilder',
    'modules/cstrike/csx/AMBuilder',
...
    'modules/ts/tsx/AMBuilder',
  ],
  { 'AMXX': AMXX }
)
```

and add your `modules/czfun/AMBuilder` file path (which locate from ./amxmodx direcotry) at bottom, like this:

```python
builder.RunBuildScripts(
  [
    'amxmodx/AMBuilder',
    'compiler/amxxpc/AMBuilder',
    'compiler/libpc300/AMBuilder',
    'modules/cstrike/cstrike/AMBuilder',
    'modules/cstrike/csx/AMBuilder',
...
    'modules/ts/tsx/AMBuilder',
    'modules/czfun/AMBuilder',
  ],
  { 'AMXX': AMXX }
)
```

## run ambuild to compile

on windows, you should use `x86 Native Tools Command Prompt for VS 2017` cmd tool to be type command.

It is a shortcut you can find it in "start menu" -> "Visual Studio 2017" (Maybe another versions).

and also, you should set the HLSDK and METAMOD env variable which target to hlsdk and metamod-hl1 folder.

> when start the cmd tool, witch at C driver when start, you can change to D driver using `D:` command.

on linux, you just do it.

```bash
# in your amxmodx sdk root folder make a dir named build
mkdir build

cd build

python ../configure.py

ambuild
```

compile successful, copy the `amxmodx/build/modules/mymodule2/mymodule2_amxx/czfun_amxx.dll` or `czfun_amxx_i386.so` to you cs1.6 server and test it!!!
