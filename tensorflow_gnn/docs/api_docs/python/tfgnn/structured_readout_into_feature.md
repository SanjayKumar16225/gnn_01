# tfgnn.structured_readout_into_feature

[TOC]

<!-- Insert buttons and diff -->

<table class="tfo-notebook-buttons tfo-api nocontent" align="left">
<td>
  <a target="_blank" href="https://github.com/tensorflow/gnn/tree/master/tensorflow_gnn/graph/readout.py#L272-L354">
    <img src="https://www.tensorflow.org/images/GitHub-Mark-32px.png" />
    View source on GitHub
  </a>
</td>
</table>

Reads out a feature value from select nodes (or edges) in a graph.

<pre class="devsite-click-to-copy prettyprint lang-py tfo-signature-link">
<code>tfgnn.structured_readout_into_feature(
    graph: <a href="../tfgnn/GraphTensor.md"><code>tfgnn.GraphTensor</code></a>,
    key: str,
    *,
    feature_name: const.FieldName,
    new_feature_name: Optional[const.FieldName] = None,
    remove_input_feature: bool = False,
    overwrite: bool = False,
    readout_node_set: const.NodeSetName = &#x27;_readout&#x27;,
    validate: bool = True
) -> <a href="../tfgnn/GraphTensor.md"><code>tfgnn.GraphTensor</code></a>
</code></pre>

<!-- Placeholder for "Used in" -->

This helper function works like
<a href="../tfgnn/structured_readout.md"><code>tfgnn.structured_readout()</code></a>
(see there), except that it does not return the readout result itself but a
modified `GraphTensor` in which the readout result is stored as a feature on the
`readout_node_set`.

<!-- Tabular view -->

 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Args</h2></th></tr>

<tr>
<td>
`graph`<a id="graph"></a>
</td>
<td>
A scalar GraphTensor with the auxiliary graph pieces required by
<a href="../tfgnn/structured_readout.md"><code>tfgnn.structured_readout()</code></a>.
</td>
</tr><tr>
<td>
`key`<a id="key"></a>
</td>
<td>
A string key to select between possibly multiple named readouts
(such as `"source"` and `"target"` for link prediction).
</td>
</tr><tr>
<td>
`feature_name`<a id="feature_name"></a>
</td>
<td>
The name of a feature to read out from, as with
<a href="../tfgnn/structured_readout.md"><code>tfgnn.structured_readout()</code></a>.
</td>
</tr><tr>
<td>
`new_feature_name`<a id="new_feature_name"></a>
</td>
<td>
The name of the feature to add to `readout_node_set`
for storing the readout result. If unset, defaults to `feature_name`.
It is an error if the added feature already exists on `readout_node_set`
in the input `graph`, unless `overwrite=True` is set.
</td>
</tr><tr>
<td>
`remove_input_feature`<a id="remove_input_feature"></a>
</td>
<td>
If set, the given `feature_name` is removed from the
node (or edge) set(s) that supply the input to
<a href="../tfgnn/structured_readout.md"><code>tfgnn.structured_readout()</code></a>.
</td>
</tr><tr>
<td>
`overwrite`<a id="overwrite"></a>
</td>
<td>
If set, allows overwriting a potentially already existing
feature `graph.node_sets[readout_node_set][new_feature_name]`.
</td>
</tr><tr>
<td>
`readout_node_set`<a id="readout_node_set"></a>
</td>
<td>
A string, defaults to `"_readout"`. This is used as the
name for the readout node set and as a name prefix for its edge sets.
See <a href="../tfgnn/structured_readout.md"><code>tfgnn.structured_readout()</code></a> for more.
</td>
</tr><tr>
<td>
`validate`<a id="validate"></a>
</td>
<td>
Setting this to false disables the validity checks of
<a href="../tfgnn/structured_readout.md"><code>tfgnn.structured_readout()</code></a>. This is strongly discouraged, unless
great care is taken to run <a href="../tfgnn/validate_graph_tensor_for_readout.md"><code>tfgnn.validate_graph_tensor_for_readout()</code></a>
earlier on structurally unchanged GraphTensors.
</td>
</tr>
</table>

<!-- Tabular view -->

 <table class="responsive fixed orange">
<colgroup><col width="214px"><col></colgroup>
<tr><th colspan="2"><h2 class="add-link">Returns</h2></th></tr>
<tr class="alt">
<td colspan="2">
A `GraphTensor` like `graph`, with the readout result stored as
`.node_sets[readout_node_set][new_feature_name]` and possibly the
readout inputs removed (see `remove_input_feature`).
</td>
</tr>

</table>
