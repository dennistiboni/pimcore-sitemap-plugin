Pimcore Sitemap Plugin
======================
XML sitemap generator for Pimcore. Built from the document tree.

## Installation
1. Run the command `composer require dennistiboni/pimcore-sitemap-plugin`
2. Enable the plugin from Extras => Extensions on Pimcore admin panel 
3. Click install to set up `sitemap_exclude` property 

## Pimcore Sitemap Plugin Settings 
1. Set the name of the domain at Pimcore system settings below the Website tab
2. Set up environment to Production at Pimcore System Settings below the Debug tab
3. Add the predefined property, `sitemap_exclude`, to every page that you want to exclude from the sitemap 
    
## Additional Settings
Using language in subfolder and get each sitemap:
    
    - Site1.com (add property => split_sitemap_language = true] )
        - en
        - it
        - fr
        
The generated sitemaps file is save onto 

`/website/static/sitemap/site1-com/sitemap-en.xml` 


### Generate sitemap on the fly

In your Controller use the sitemapAction, the public method getSitemapXml
passing the root navigation node.

```

public function sitemapAction()
{
    $this->disableLayout();
    $this->disableViewAutoRender();
    
    if ($this->mainNavStartNode){
        $sitemap = new \Byng\Pimcore\Sitemap\Generator\SitemapGenerator();
        echo $sitemap->getSitemapXml($this->mainNavStartNode );
    }
    
    return NULL;
}
```
        
    
## License

MIT