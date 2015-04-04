+++
date = "2015-04-02T14:48:15-04:00"
title = "Setting up a blog with Hugo and Heroku"
description = "My First Post!"
+++

Today I will walk you through how to set up a blog with Hugo and host it on Heroku. 

Hugo is a static website engine that takes raw content in various formats (like markdown
 <sup id='fnref:1'>
 	<a href='#fn:1' rel='footnote'>1</a>
</sup>)



___


<pre>
<code class='c#'>
public class ReadOnlyPropertyGrid : PropertyGrid
{
  private bool _readOnly;
  public bool ReadOnly
  {
    get { return _readOnly; }
    set
    {
      _readOnly = value;
      this.SetObjectAsReadOnly(this.SelectedObject, _readOnly);
    }
  }

  protected override void OnSelectedObjectsChanged(EventArgs e)
  {
    this.SetObjectAsReadOnly(this.SelectedObject, this._readOnly);
    base.OnSelectedObjectsChanged(e);
  }

  private void SetObjectAsReadOnly(object selectedObject, bool isReadOnly)
  {
    if (this.SelectedObject != null)
    {
      TypeDescriptor.AddAttributes(this.SelectedObject, new Attribute[] { new ReadOnlyAttribute(_readOnly) });
      this.Refresh();
    }
  }
}
</code>

</pre>
<div class="footnotes"><ol>
    <li class="footnote" id="fn:1">
    <p>
    *   Bird
    *   Magic

    <a href='#fnref:1' title='return to article' class="reversefootnote">&nbsp;</a></p>
    </li>
</ol></div>