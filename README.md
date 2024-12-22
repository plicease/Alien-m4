# Alien::m4 ![linux](https://github.com/PerlAlien/Alien-m4/workflows/linux/badge.svg) ![macos](https://github.com/PerlAlien/Alien-m4/workflows/macos/badge.svg) ![windows](https://github.com/PerlAlien/Alien-m4/workflows/windows/badge.svg) ![msys2-mingw](https://github.com/PerlAlien/Alien-m4/workflows/msys2-mingw/badge.svg)

Find or build GNU m4

# SYNOPSIS

From a Perl script

```perl
use Alien::m4;
use Env qw( @PATH );
unshift @PATH, Alien::m4->bin_dir;  # m4 is now in your path
```

From Alien::Base Build.PL

```perl
use Alien:Base::ModuleBuild;
my $builder = Module::Build->new(
  ...
  alien_bin_requires => {
    'Alien::m4' => '0.07',
  },
  ...
);
$builder->create_build_script;
```

# DESCRIPTION

This package can be used by other CPAN modules that require GNU m4.

# METHODS

## exe

```perl
my $m4 = Alien::m4->exe;
```

Returns the "name" of m4.  Normally this is `m4`, but on some platforms
it may be gm4 or gnum4, or whatever is specified by `$ENV{M4}`.

# HELPERS

## m4

```
%{m4}
```

Returns the name of the m4 command.  Usually just `m4`.

# CAVEATS

Why GNU m4?  Many Unixen come with BSD or other variants of m4 which are
perfectly good.  Unfortunately, the main use case for this module is
[Alien::Autotools](https://metacpan.org/pod/Alien::Autotools) and friends.  Autoconf requires the GNU m4, probably
for political reasons, possibly for technical reasons.  If you are using
one of these Unixen, don't despair, you can usually install the GNU
version of m4 either by building from source or by installing a binary
package, with either the name `gm4` or `gnum4`, and this module will
find it, and [Alien::Autotools](https://metacpan.org/pod/Alien::Autotools) will be able to use it.

# AUTHOR

Graham Ollis <plicease@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2017-2024 by Graham Ollis.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
