coala 0.7.0 - baloo
===================

::

              ,o8b,         .o88Oo._
             P    d        d8P         .ooOO8bo._
            d'    p        88                  '*Y8bo.
           .Y    ."         YA                      '*Y8b   __
       db, d" _ooQ.dPQ,     YA                        68o68**8Oo.
     .8'  YI.Y"   b   B      "8D                       *"'    "Y8o
    .Y    ;L 8,    Yq.8       Y8     'YB                       .8D
    B .db_.L  q,   q "q       '8               d8'             8D
    8"    qp   8,  8           8       d8888b          d      AY
           8    ",dP           Y,     d888888         d'  _.oP"
           "q    8;             q.    Y8888P'        d8
            '8    b              "q.  `Y88P'       d8"
             'D,  ,8                Y           ,o8P
               'odY'                     oooo888P"

(Release logo by Fabian Neuschmidt)

For this release, 32 people from all over the world have contributed about 200
commits over almost two months.

The focus of this release is certainly on the usability of coala. Usability
testing has made us aware of some important difficulties, users have to face
when trying out coala. We have implemented a lot of countermeasures to lower
this barrier.

The changelog below summarizes the most important user facing changes. Not
listed are especially lots of internal improvements and documentation fixes.

New Features:

- `Shell Autocompletion <http://coala.readthedocs.io/en/latest/Users/Tutorials/Shell_Autocompletion.html>`_
- Patches are shown without prompting the user if small enough, otherwise
  diffstats.
- Bears have metadata and can be browsed. Browse the
  `bear documentation <https://github.com/coala-analyzer/bear-docs>`_
  repository for more information on all the bears.
- Lots of usability improvements! coala will suggest using certain options if
  no meaningful configuration was supplied.
- The help was revamped completely and is way easier to read.
- A ``--verbose`` alias is available for ``-L DEBUG``.
- The ``default_actions`` setting accepts globs for bears now.
- The ``--apply-patches`` argument was added to automatically apply all
  patches.
- coala supports experimental caching. This can lower the run time to a
  fraction of the time needed to perform the full analysis. It will be enabled
  by default in the next release. To use it, invoke coala with
  ``--changed-files``.
- Bear showing is divided into a new set of settings: ``--show-bears`` shows
  all bears, ``--filter-by-language`` allows to filter them, ``--show-details``
  and ``--show-description`` allow changing verbosity of the output.

Feature Removals:

- Tagging was removed.
- ``linter`` does no longer show the executable of the bear by default.

Performance Improvements:

- Globs will be internally cached now so they don't need to be retranslated
  every time. This may show improvements of several seconds when working with
  a large set of files.
- coala supports experimental caching. See ``New Features`` for more
  information.
- coala does not delete ``*.orig`` files on startup anymore. This was a huge
  performance hit especially on HDDs or big file trees. The cleanup can be
  performed manually by running ``coala-delete-orig``. Instead coala will
  keep track of ``*.orig`` files more smartly.

Bugfixes:

- ``**.py`` can again be used instead ``**/*.py``.
- If errors happen before the initialization of logging, tracebacks will be
  shown.

For bear writers:

- Bears can have a number of attributes now, including author information,
  supported languages or categories. A requirements attribute will help
  generating requirements definition files more easily in the future.
- The ``linter`` wrapper provides a ``result_severity`` and a
  ``result_message`` parameter now.
- Bears can now delete and rename files.
- The ``LanguageDefinition`` doesn't need a ``language_family`` anymore to
  load language definitions.
- Results can be created directly from the Bear class more conveniently
  with ``self.new_result(...)``.

coala 0.6.0 - honeybadger
=========================

::

     .o88Oo._                                .".      "     .".
    d8P         .ooOO8bo._                   dPo.    O#O   .oPb
    88                  '*Y8bo.              88o.   .o#o.  .o88
    YA                      '*Y8b   __       Y88o.   .8.  .o88Y
     YA                        68o68**8Oo.    W8888O888888888W
      "8D                       *"'    "Y8o    w8888'88'8888w
       Y8     'YB                       .8D     `o88:88:88o'
       '8               d8'             8D       .O8`88'8O.
        8       d8888b          d      AY        oO8I88I8Oo
        Y,     d888888         d'  _.oP"         oO8|88|Oo
         q.    Y8888P'        d8                 oO8.88.8Oo
          "q.  `Y88P'       d8"                  .oO.88.Oo.
            Y           ,o8P                    .oO888888Oo.
                  oooo888P"                    .oO8      8Oo.
                                               +oO8+    +8Oo+
                                               'bo.      .od'

This release is shaped a lot by working on high quality bear writing tools. Our
codebase has matured further (improved tests, various internal improvements)
and key features for writing and organizing bears were introduced.

Over the last 1.5 months, 22 unique contributors have helped us at the coala
core project.

This time, the release logo is carefully hand crafted by Max Scholz!

New features:

-  Smart globbing: use backslashes without an extra escape now if they don't
   escape delimiters.
-  Results now can have additional information appended.
-  Bears expose information on which languages they support. You can query for
   bears e.g. with ``coala --show-language-bears C++`` for C++.

Bugfixes:

-  Linters suppress the output correctly now when checking for linter
   availibility. (https://github.com/coala-analyzer/coala/issues/1888)
-  The result filter algorithms can handle file additions and deletions now.
   (https://github.com/coala-analyzer/coala/issues/1866)
-  Ignore statements without a stop statement are now accepted as well
   (https://github.com/coala-analyzer/coala/issues/2003).

For bear writers:

-  A tutorial for managing bear dependencies is available in our documentation
   now.
-  The Result object has a field ``additional_info`` which can be used to give
   an elaborate description of the problem.
-  A ``typechain()`` function is now available for easy conditional type
   conversion. (https://github.com/coala-analyzer/coala/issues/1859)
-  Bears have a ``name()`` shortcut now which provides the bear class name.
-  A ``get_config_directory()`` function is available that returns the root
   directory of the project guessed by coala or provided (overridden) by the
   user.
-  A new ``linter`` decorator makes it even easier to write new linter
   wrappers. (https://github.com/coala-analyzer/coala/issues/1928)

Notable internal/API changes:

-  ``FunctionMetadata`` has a new ``merge`` function that can be used to merge
   function signatures and documentation comments.

coala 0.5.0 - joey
==================

::

     .o88Oo._
    d8P         .ooOO8bo._
    88                  '*Y8bo.
    YA                      '*Y8b   __
     YA                        68o68**8Oo.
      "8D                       *"'    "Y8o
       Y8     'YB                       .8D
       '8               d8'             8D
        8       d8888b          d      AY
        Y,     d888888         d'  _.oP"
        ,q.    Y8888P'        d8,
        d "q.  `Y88P'       d8" b
        Y,   Y           ,o8P  ,Y
        8q.       oooo888P"   .p8
        8 "qo._           _.op" 8
        8   '"P8866ooo6688P"'   8
        8                       8
        8                       8
        8.                     .8
        "b                     d"
        'b                     d'
         8                     8
         q.                   .p
          q.                 .p
          "qo._           _.op"
            '"P8866ooo6688P"'

With this release we declare coala proudly as beta. Most features are now
available and coala is ready for daily use.

All bears have been moved out of coala into the ``coala-bears`` package. If you
want to develop bears for coala, you can now install it without the bears just
as before. If you want to use the coala official bears, make sure to install the
``coala-bears`` package and if needed follow the instructions to install linters
needed by the bears for your language.

According to ``git shortlog -s -n 5fad168..`` 56 people contributed to this
release. We sadly cannot name all the new coalaians here but every single
one of them helped making coala as awesome and polished as it is today.

New features:

-  ``--no-config`` allows to ignore existing coafiles in the current directory.
   (https://github.com/coala-analyzer/coala/issues/1838)
-  In-file ignore directives now support globs.
   (https://github.com/coala-analyzer/coala/issues/1781)
-  ``coala-json`` supports the ``--relpath`` argument so the JSON output can be
   moved to other systems reasonably.
   (https://github.com/coala-analyzer/coala/issues/1593)
-  ``--bear-dirs`` are now searched recursively. They are also added to the
   Python PATH so imports relative to a given bear directory work.
   (https://github.com/coala-analyzer/coala/issues/1711,
    https://github.com/coala-analyzer/coala/issues/1712)
-  ``coala-format`` exposes the ``{severity_str}`` so you can get a human
   readable severity in your self formatted result representation.
   (https://github.com/coala-analyzer/coala/issues/1313)
-  Spaces and tabs are highlighted in the CLI to make whitespace problems
   obvious. (https://github.com/coala-analyzer/coala/issues/606)
-  Actions that are not applicable multiple times are not shown after applying
   them anymore. (https://github.com/coala-analyzer/coala/issues/1064)
-  Documentation about how to add coala as a pre commit hook has been added:
   http://coala.readthedocs.org/en/latest/Users/Git_Hooks.html
-  Actions emit a success message now that is shown to the user and improves
   usability and intuitivity of actions.
-  A warning is emitted if a bear or file glob does not match any bears or
   files.
-  ``coala-json`` supports now a ``--text-logs`` argument so you can see your
   logs in realtime, outside the JSON output if requested. You can output the
   JSON output only into a file with the new ``-o`` argument.
   (https://github.com/coala-analyzer/coala/issues/847,
    https://github.com/coala-analyzer/coala/issues/846)
-  ``coala-ci`` yields a beautiful output now, showing the issues
   noninteractively. (https://github.com/coala-analyzer/coala/issues/1256)
-  A ``coala-delete-orig`` script is now available to delete autogenerated
   backup files which were created when a patch was applied. This is called
   automatically on every coala run.
   (https://github.com/coala-analyzer/coala/issues/1253)
-  The ``--limit-files`` CLI argument was introduced which is especially useful
   for writing performant editor plugins.

Exitcode changes:

-  coala returns ``5`` if patches were applied successfully but no other results
   were yielded, i.e. the code is correct after the execution of coala but was
   not before.
-  coala returns ``4`` now if executed with an unsupported python version.

Bugfixes:

-  The ``appdirs`` module is now used for storing tagged data.
   (https://github.com/coala-analyzer/coala/issues/1805)
-  Package version conflicts are now handled with own error code ``13``.
   (https://github.com/coala-analyzer/coala/issues/1748)
-  Previously inputted values for actions are not stored any more if the action
   fails.
   (https://github.com/coala-analyzer/coala/issues/1825)
-  coala doesn't crash any more on Windows when displaying a diff. Happened due
   to the special chars used for whitespace-highlighting Windows terminals do
   not support by default.
   (https://github.com/coala-analyzer/coala/issues/1832)
-  Escaped characters are written back to the ``.coafile`` correctly.
   (https://github.com/coala-analyzer/coala/issues/921)
-  ``coala-json`` doesn't show logs when invoked with ``-v`` or ``-h`` anymore
   (https://github.com/coala-analyzer/coala/issues/1377)
-  Keyboard interrupts are handled more cleanly.
   (https://github.com/coala-analyzer/coala/issues/871)
-  Tagging will only emit a warning if the data directory is not writable
   instead of erroring out.
   (https://github.com/coala-analyzer/coala/issues/1050)
-  Unicode handling has been improved.
   (https://github.com/coala-analyzer/coala/issues/1238)
-  Cases where ``--find-config`` has not found the configuration correctly have
   been resolved. (https://github.com/coala-analyzer/coala/issues/1246)
-  Some cases, where result ignoring within files didn't work have been
   resolved. (https://github.com/coala-analyzer/coala/issues/1232)

For bear writers:

-  A new built-in type is available from ``Setting`` for using inside ``run()``
   signature: ``url``.
-  ``Lint`` based bears have a new argument which can be set to test whether a
   command runs without errors. This can be used to check for example the
   existence of a Java module.
   (https://github.com/coala-analyzer/coala/issues/1803)
-  The ``CorrectionBasedBear`` and ``Lint`` class have been merged into the new
   and more powerful ``Lint`` class to make linter integration even easier. It
   also supports you if you need to generate an actual configuration file for
   your linter.
-  ``LocalBearTestHelper`` as well as the ``verify_local_bear`` have been
   revamped to make it even easier to test your bears and debug your tests.
-  File dictionaries are now given as tuples and are thus not modifyable.
-  A number of new tutorials about bear creation have been written.
-  Bears can now be registered at coala and thus be distributed as own packages.

Notable internal changes:

-  API documentation is now available at
   http://coala.readthedocs.org/en/latest/API/modules.html
-  coala switched to PyTest. Our old own framework is no longer maintained.
   (https://github.com/coala-analyzer/coala/issues/875)
-  As always loads of refactorings to make the code more stable, readable and
   beautiful!
-  The main routines for the coala binaries have been refactored for less
   redundancy. If you are using them to interface to coala directly, please
   update your scripts accordingly.
-  Loads of new integration tests have been written. We're keeping our 100% test
   coverage promise even for all executables now.

coala 0.4.0 - eucalyptus
========================

::

        88        .o88Oo._
       8 |8      d8P         .ooOO8bo._
      8  | 8     88                  '*Y8bo.
      8\ | /8    YA                      '*Y8b   __
     8  \|/ 8     YA                        68o68**8Oo.
     8\  Y  8      "8D                       *"'    "Y8o
     8 \ | /8       Y8     'YB                       .8D
    8   \|/ /8     '8               d8'             8D
    8\   Y / 8       8       d8888b          d      AY
    8 \ / /  8       Y,     d888888         d'  _.oP"
    8  \|/  8         q.    Y8888P'        d8
    8   Y   8          "q.  `Y88P'       d8"
     8  |  8             Y           ,o8P
      8 | 8                    oooo888P"

New features:

-  Auto-apply can be enabled/disabled through the ``autoapply`` setting
   in a coafile.
-  Auto-applied actions print the actual file where something happened.
-  A new bear was added, the GitCommitBear! It allows to check your
   current commit message at HEAD from git!
-  Filenames of results are now printed relatively to the execution
   directory. (https://github.com/coala-analyzer/coala/issues/1124)

Bugfixes:

-  coala-json outputted results for file-ranges that were excluded.
   (https://github.com/coala-analyzer/coala/issues/1165)
-  Auto-apply actions that failed are now marked as unprocessed so the
   user can decide manually what he wants to do with them.
   (https://github.com/coala-analyzer/coala/issues/1202)
-  SpaceConsistencyBear: Fixed misleading message when newline at EOF is
   missing. (https://github.com/coala-analyzer/coala/issues/1185)
-  Results from global bears slipped through our processing facility.
   Should not happen any more.

coala 0.3.0 - platypus
======================

We are dropping Python 3.2 support (and so PyPy). Also we are removing
translations, the default language is English.

This release contains these following feature changes:

-  Auto-apply feature added! Results can directly be processed without
   user interaction specifying the desired action!
-  A missing coafile that is explicitly wanted through the ``--config``
   flag throws an error instead of a warning. Only default coafile names
   (ending with ``.coafile``) raise a warning.
-  Various new bears integrating existing linter tools, e.g. for C/C++,
   Python, Ruby, JSON and many more!
-  Allow to ignore files inside the coafile.
-  Results can now be stored and tagged with an identifier for accessing
   them later.
-  OpenEditorAction lets the user edit the real file instead of a
   temporary one.
-  All usable bears can now be shown with ``--show-all-bears``.
-  Only ``#`` is supported for comments in the configuration file
   syntax.
-  Multiple actions can now be executed on the CLI.
-  Patches can now be shown on the CLI.
-  A ``coala-format`` binary was added that allows customized formatting
   for results to ease integration in other systems.
-  Printing utilities have moved into the PyPrint library.

Bear API changes:

-  A bear can implement ``check_prerequisites`` to determine whether it
   can execute in the current runtime.
-  The PatchResult class was merged into the Result class.

Bear changes:

-  SpaceConsistencyBear offers more verbose and precise information
   about the problem.

coala 0.2.0 - wombat
====================

::

     .o88Oo._
    d8P         .ooOO8bo._
    88                  '*Y8bo.
                          '*Y8b   __
     YA                        68o68**8Oo.     _.o888PY88o.o8
      "8D                       *"'    "Y8o.o88P*'         Y.
       Y8     'YB                       .8D                 Y.
       '8               d8'             8D             o     8
        8       d8888b          d      AY   o               d'
        Y,     d888888         d'  _.oP"         d88b       8
         q.    Y8888P'        d8       Y,       d8888       P
          "q.  `Y88P'       d8"         q.      Y888P     .d'
             Y           ,o8P            "q      `"'    ,oP
                  oooo888P"               `Y         .o8P"
                                              8ooo888P"

This release features the following feature changes:

-  ``--find-config`` flag: Searches for .coafile in all parent
   directories.
-  Add code clone detection bears and algorithms using CMCD approach.
-  Console color gets properly disabled now for non-supporting platforms
   (like Windows).
-  coala results can be outputted to JSON format using the
   ``coala-json`` command.
-  Automatically add needed flags to open a new process for some
   editors.
-  Save backup before applying actions to files.
-  Return nonzero when erroring or yielding results.
-  Write newlines before beginning new sections in coafiles when
   appropriate.
-  The default\_coafile can now be used for arbitrary system-wide
   settings.
-  coala can now be configured user-wide with a ~/.coarc configuration
   file.
-  Manual written documentation is now hosted at http://coala.rtfd.org/.
-  Changed logging API in Bears (now: debug/warn/err).
-  clang python bindings were added to the bearlib.
-  Exitcodes were organized and documented.
   (http://coala.readthedocs.org/en/latest/Users/Exit_Codes.html)
-  Handling of EOF/Keyboard Interrupt was improved.
-  Console output is now colored.
-  Bears can now easily convert settings to typed lists or dicts.
-  Bears have no setUp/tearDown mechanism anymore.
-  Colons cannot be used for key value seperation in configuration files
   anymore as that clashes with the new dictionary syntax. Use ``=``
   instead.
-  The ``--job-count`` argument was removed for technical reasons. It
   will be re-added in the near future.
-  A ``--show-bears`` parameter was added to get metainformation of
   bears.
-  The coala versioning scheme was changed to comply PEP440.
-  ``coala --version`` now gives the version number. A released ``dev``
   version has the build date appended, 0 for local versions installed
   from source.
-  A ``coala-dbus`` binary will now be installed that spawns up a dbus
   API for controlling coala. (Linux only.)
-  The StringProcessing libary is there to help bear writers deal with
   regexes and similar things.
-  A new glob syntax was introduced and documented.
   (http://coala.readthedocs.org/en/latest/Users/Glob_Patterns.html)
-  The ``--apply-changes`` argument was removed as its concept does not
   fit anymore.
-  Bears can now return any iterable. This makes it possible to
   ``yield`` results.

New bears:

-  ClangCloneDetectionBear
-  LanguageToolBear
-  PyLintBear

Infrastructural changes:

-  Tests are executed with multiple processes.
-  Branch coverage raised to glorious 100%.
-  We switched from Travis CI to CircleCI as Linux CI.
-  AppVeyor (Windows CI) was added.
-  Travis CI was added for Mac OS X.
-  Development releases are automatically done from master and available
   via ``pip install coala --pre``.
-  Rultor is now used exclusively to push on master. Manual pushes to
   master are not longer allowed to avoid human errors. Rultor deploys
   translation strings to Zanata and the PyPI package before pushing the
   fastforwarded master.

Internal code changes:

-  Uncountable bugfixes.
-  Uncountable refactorings touching the core of coala. Code has never
   been more beautiful.

We are very happy that 7 people contributed to this release, namely
Abdeali Kothari, Mischa Krüger, Udayan Tandon, Fabian Neuschmidt, Ahmed
Kamal and Shivani Poddar (sorted by number of commits). Many thanks go
to all of those!

coala's code base has grown sanely to now over 12000 NCLOC with almost
half of them being tests.

We are happy to announce that Mischa Krüger is joining the maintainers
team of coala.

Furthermore we are happy to announce basic Windows and Mac OS X support.
This would not have been possible without Mischa and Abdeali. coala is
fully tested against Python 3.3 and 3.4 on Windows and 3.2, 3.3, 3.4 and
Pypy3 on Mac while not all builtin bears are tested. coala is also
tested against Pypy3 and Python 3.5 beta (in addition to 3.3 and 3.4) on
Linux.

coala 0.1.1 alpha
=================

This patch release fixes a major usability issue where data entered into
the editor may be lost.

For more info, see release 0.1.0.

coala 0.1.0 alpha
=================

Attention: This release is old and experimenental.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

coala 0.1 provides basic functionality. It is not feature complete but
already useful according to some people.

For information about the purpose of coala please look at the README
provided with each source distribution.

Note that this is a prerelease, thus this release will be supported with
only important bugfixes for limited time (at least until 0.2.0 is
released). Linux is the only supported platform.

Documentation for getting started with coala is provided here:
https://github.com/coala-analyzer/coala/blob/v0.1.0-alpha/TUTORIAL.md

If you want to write static code analysis routines, please check out
this guide:
https://github.com/coala-analyzer/coala/blob/v0.1.0-alpha/doc/getting\_involved/WRITING\_BEARS.md

We love bugs - if you find some, be sure to share them with us:
https://github.com/coala-analyzer/coala/issues
