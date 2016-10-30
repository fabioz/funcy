    .. <script src="http://code.jquery.com/jquery-1.12.4.min.js" integrity="sha256-ZosEbRLbNQzLpnKIkEdrPv7lOy9C27hHQ+Xp8a4MxAQ=" crossorigin="anonymous"></script>

.. raw:: html

    <script src="_static/nhpup_1.1.js"></script>
    <style>
    #pup {
      position:absolute;
      z-index:200; /* aaaalways on top*/
      padding: 3px 7px 4px;
      margin-left: 5px;
      margin-top: 15px;
      border-radius: 3px;
      background-color: #343131;
      color: #b3b3b3;
      font-size: 0.95em;
    }
    .descriptions {display: none}
    .rst-content table.docutils td {vertical-align: top}
    .wy-table-responsive table td {white-space: normal}
    .rst-content tt {font-size: 100%; padding: 0px 2px; border: none; background: none; line-height: 20px}

    #pup strong, #pup b {color: #ddd}
    #pup em {color: #3591CC; font-weight: bold}
    #pup code {background: transparent; border: none}
    </style>

    <script>
        function defer(method) {
            if (window.jQuery)
                method();
            else
                setTimeout(function() { defer(method) }, 50);
        }
        defer(function () {
            // Strip parentheses
            $('.py-func .pre').each(function () {
                var text = $(this).text();
                if (text.substr(-2) === '()') $(this).text(text.substr(0, text.length-2));
            })

            nhpup.initialize()
            $('.descriptions div').each(function () {
                var name = this.getAttribute('name');
                var width = this.getAttribute('width') || 260;
                $('a[title='+name+']').on('mouseover', nhpup.popup(this.innerHTML, {width: width})).removeAttr('title');
            })
        })
    </script>


.. _cheatsheet:

Cheatsheet
==========

Hover over function to get description.


Sequences
---------

========== ==============================================================
Create     :func:`count` :func:`cycle` :func:`repeat` :func:`repeatedly` :func:`iterate` :func:`re_iter` :func:`re_all`
Access     :func:`first` :func:`second` :func:`last` :func:`nth` :func:`some` :func:`take`
Slice      :func:`take` :func:`drop` :func:`rest` :func:`butlast` :func:`takewhile` :func:`dropwhile` :func:`split_at` :func:`split_by`
Transform  :func:`map` :func:`mapcat` :func:`keep` :func:`pluck` :func:`pluck_attr` :func:`invoke`
Filter     :func:`filter` :func:`remove` :func:`keep` :func:`distinct` :func:`where` :func:`without`
Join       :func:`cat` :func:`concat` :func:`flatten` :func:`mapcat` :func:`interleave` :func:`interpose`
Partition  :func:`chunks` :func:`partition` :func:`partition_by` :func:`split_at` :func:`split_by`
Group      :func:`split` :func:`count_by` :func:`group_by` :func:`group_by_keys` :func:`group_values`
Aggregate  :func:`ilen` :func:`reductions` :func:`sums` :func:`all` :func:`any` :func:`none` :func:`one`
Iterate    :func:`pairwise` :func:`with_next` :func:`with_prev` :func:`izip_values` :func:`izip_dicts` :func:`tree_leaves` :func:`tree_nodes`
========== ==============================================================


Collections
-----------

========== ==============================================================
Join       :func:`merge` :func:`merge_with` :func:`join` :func:`join_with`
Transform  :func:`walk` :func:`walk_keys` :func:`walk_values`
Filter     :func:`select` :func:`select_keys` :func:`select_values` :func:`compact`
Dict       :func:`flip` :func:`zipdict` :func:`pluck` :func:`where` :func:`itervalues` :func:`iteritems` :func:`izip_values` :func:`izip_dicts`
Misc       :func:`empty` :func:`get_in` :func:`set_in` :func:`update_in`
========== ==============================================================


Functions
---------

========== ==============================================================
Create     :func:`identity` :func:`constantly` :func:`func_partial` :func:`partial` :func:`rpartial` :func:`iffy` :func:`caller` :func:`re_finder` :func:`re_tester`
Transform  :func:`complement` :func:`iffy` :func:`autocurry` :func:`curry` :func:`rcurry`
Combine    :func:`compose` :func:`rcompose` :func:`juxt` :func:`all_fn` :func:`any_fn` :func:`none_fn` :func:`one_fn` :func:`some_fn`
========== ==============================================================


Other topics
------------

================== ==============================================================
Content tests      :func:`all` :func:`any` :func:`none` :func:`one` :func:`is_distinct`
Type tests         :func:`isa` :func:`is_iter` :func:`is_list` :func:`is_mapping` :func:`is_seq` :func:`is_seqcoll` :func:`is_seqcont` :func:`iterable` :func:`is_set` :func:`is_tuple`
Decorators         :func:`decorator<funcy.decorator>` :func:`wraps<funcy.wraps>` :func:`unwrap<funcy.unwrap>` :func:`autocurry`
Control flow       :func:`once` :func:`once_per` :func:`once_per_args` :func:`collecting` :func:`joining` :func:`post_processing`
Error handling     :func:`retry` :func:`silent` :func:`ignore` :func:`suppress` :func:`limit_error_rate` :func:`fallback` :func:`raiser`
Debugging/Logging  :func:`tap` :func:`log_calls` :func:`log_durations` :func:`log_enters` :func:`log_enters` :func:`log_errors` :func:`log_iter_durations`
Caching            :func:`memoize` :func:`cache` :func:`cached_property` :func:`make_lookuper` :func:`silent_lookuper`
Regexes            :func:`re_find` :func:`re_test` :func:`re_all` :func:`re_iter` :func:`re_finder` :func:`re_tester`
Strings            :func:`cut_prefix` :func:`cut_suffix` :func:`str_join`
Objects            :func:`cached_property` :func:`monkey` :func:`invoke` :func:`pluck_attr`
Primitives         :func:`isnone` :func:`notnone` :func:`inc` :func:`dec` :func:`even` :func:`odd`
================== ==============================================================


.. raw:: html

    <div class="descriptions">

    <div name="count" width="280">
    <b>count<em>(start=0, step=1)</em></b><br><br>
    Makes infinite iterator of values:<br>
    <code><em>start</em>, <em>start</em> + <em>step</em>, <em>start</em> + 2*<em>step</em>, ...</code>
    </div>

    <div name="first">
    <b>first<em>(seq)</em></b><br><br>
    Returns first item in sequence.<br>Returns <code>None</code> if sequence is empty.
    </div>

    <div name="map">
    <strong>map<em>(f, *seqs)</em><br>imap<em>(f, *seqs)</em></strong><br><br>
    Extended versions of <b>map()</b> and <b>imap()</b>
    </div>

    <div name="constantly">
    <strong>constantly<em>(x)</em></strong><br><br>
    Creates function accepting any args, but always returning <em>x</em>.
    </div>
    </div>