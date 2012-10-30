#Multiple Textstring

`Returns: XML`

The Multiple Textstring data-type enables a content editor to make a list of text items. For best use with an unordered-list.

##Settings

There are two settings for Multiple Textstring which allow the setting of the minimum and maximum (-1 unlimited) number of items to display.

![Multiple Textstring Data Type Definition](images/Multiple-Textstring-Settings.jpg?raw=true)

##Content Example 

![Multiple Textstring Content Example](images/Multiple-Textstring-Content.jpg?raw=true)

##Data example

Multiple Textstring stores it's content as XML, below is an example.

	<keyFeatureList>
		<values>
			<value>Strong</value>
			<value>Flexible</value>
			<value>Efficient</value>
		</values>
	</keyFeatureList>
	

##XSLT Example

	<xsl:if test="count($currentPage/keyFeatureList/values/value) > 0">
	  <ul>
		<xsl:for-each select="$currentPage/keyFeatureList/values/value">
			<li><xsl:value-of select="current()"/></li>
		</xsl:for-each>
	  </ul>
	</xsl:if>

##Razor (DynamicXML) Example

	@inherits umbraco.MacroEngines.DynamicNodeContext
	@using umbraco.MacroEngines
	@{
		if (Model.keyFeatureList.Count() > 0){	
		  <ul>
			@foreach (var item in Model.keyFeatureList) {		
				<li>@item.InnerText</li>
			}
		  </ul>
		}
	}