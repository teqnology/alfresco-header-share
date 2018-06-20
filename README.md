Androgogic - Alfresco Header Share
==================================

This extension aims to customize the header in Alfresco 5.x using Share extension point: [Surf Extension Modules](http://docs.alfresco.com/5.0/concepts/dev-extensions-share-surf-extension-modules.html).
[Here](http://docs.alfresco.com/5.0/tasks/dev-extensions-share-tutorials-customize-header-style.html) you'll find all the steps that have been undertaken.

# Features

- Brand new Alfresco Share header style, inspired by [Material Design Lite](http://www.getmdl.io/)
- Better UX and improved readibility of menu items
- New colour scheme based on [this material palette](https://www.materialpalette.com/blue-grey/deep-orange)
- New hover effects
- New dropdown style
- New `current user status` style
- *TODO This is the first release, therefore a lot of stuff is still a WiP, like input items, buttons etc. This is not a finished product and it's still not recommended for a production environment.*

# Preview

![Custom Header](https://raw.githubusercontent.com/teqnology/alfresco-header-share/master/screenshots/screenshot.png "Andro Header preview")

# Essentials

- Alfresco Enterprise/Community 5.x
- Alfresco Maven SDK 2.1.0 ([Alfresco Maven compatibility matrix](http://docs.alfresco.com/5.0/concepts/alfresco-sdk-compatibility.html))
- [Alfresco Maven Enterprise account](http://docs.alfresco.com/5.0/concepts/alfresco-sdk-tutorials-alfresco-enterprise.html) (if using Enterprise artifacts, `pom.xml` needs to be changed accordingly).
- `alfresco-header-share.amp` found [here](https://github.com/teqnology/alfresco-header-share/blob/master/target/alfresco-header-share.amp).

# Quickstart

- Locate the AMP files inside the path:
	- `alfresco-header-share/target/alfresco-header-share.amp` you can download it from [this link](https://github.com/teqnology/alfresco-header-share/raw/master/target/alfresco-header-share.amp).
- Stop Alfresco
- Copy the `alfresco-header-share.amp` inside your alfresco `amps_share` folder
- Run `bin/apply_amps.sh` in order to install the extensions
- Start Alfresco
- Open Alfresco Share URL (eg. `http://localhost:8080/share`) and log in
- Make sure the new menu is installed
- If you don't see the new menu, open Alfresco Share module deploy page: `/share/page/modules/deploy` and make sure the `Andro Header` modules appears under `Deployed modules`.

## Quickstart for devs

- Enter the project folder and run `./run.sh` (you might need to `chmod u+x run.sh` and|or `chmod 777 run.sh` to make it executable). This will setup the SDK and the Alfresco Share on port 8081 (not Alfresco Repository or Solr).
- Wait for the startup of the webapp and then go `http://localhost:8081/share`. NOTE: For this to work you need to have an Alfresco previously running on port 8080, for example as provided by the Alfresco AMP archetype
- Import the project in your favorite IDE (with Maven integration) and start developing right away.

For additional info please refer to [Maven Alfresco SDK documentation - Share AMP Archetype](https://artifacts.alfresco.com/nexus/content/groups/public/alfresco-sdk-aggregator/latest/archetypes/share-amp-archetype/index.html).

# Source code documentation

In order to change the colour scheme just go to your share web app folder (eg. `tomcat/webapps/share`) and navigate to `css/header`. You can either create a new `header.css` file and override the current color scheme. The complete css source is:

`share/css/header/header.css`:
    
    .alfresco-share .navigation-menu {
    }
    
    .alfresco-share .title-menu {
    }
    
    .alfresco-share .alfresco-header-Header {
       background-color: #455A64;
       text-transform: uppercase;
       padding: 1em;
    }
    
    /* Sets the highlight on the menu bar items in the header bar ONLY */
    .alfresco-share .alfresco-header-Header .alfresco-menus-AlfMenuBar .dijitMenuPassive .dijitMenuItemHover {
       border-bottom: 4px solid #FF5722;
    }
    
    .alfresco-share .alf-header-menu-bar .dijitMenuItem {
       color: #CFD8DC;
    }
    
    .alfresco-share .dijitReset.dijitInline.dijitMenuItemLabel.dijitMenuItem {
      margin: 0 5px;
      padding: 2px 5px;
      text-overflow: ellipsis;
      white-space: nowrap;
      max-width: 150px;
    }
    
    
    
    /* Sets the highlight on popup menu items in the header bar ONLY. Note that we need to use "alf-header-menu-bar" and not
       just "alf-header" because the popup is not a direct child of the node set with the "alf-header" class */
    .alfresco-share .alf-header-menu-bar .alf-menu-group .dijitMenuPassive .dijitMenuItemHover,
    .alfresco-share .alf-header-menu-bar .alf-menu-group .dijitMenuItemSelected {
       background-color: #455A64;
       color: #FFFFFF;
       border-bottom: 4px solid #FF5722;
    }
    
    /* Sets the selection highlight colour on header menu items - more specific than class in AlfMenuBar */
    .alfresco-share .alfresco-header-Header .dijitReset.dijitInline.dijitMenuItemLabel.dijitMenuItemSelected.dijitMenuItem {
       background-color: #455A64;
       border-bottom: 4px solid #FF5722;
    }
    
    /* Sets the correct height for the header menu bar items. This may need to be changed for different browsers and
     * possible adjusted if items in the header are changed */
    .alfresco-share .alfresco-header-Header .dijitMenuItem {
       background-color: transparent !important;
       border-bottom: 4px solid transparent;
    }
    
    /* Sets the dark grey colour in the drop-down menus in header menus ONLY. */
    .alfresco-share .alf-header-menu-bar.alf-menu-groups {
       background-color: #455A64;
       border: none;
       box-shadow: 0.33px 2px 8px rgba(0, 0, 0, 0.3);
    }
    
    /* Sets the dark grey colour in the menu groups in the header menu ONLY */
    .alfresco-share .alf-header-menu-bar .dijitMenuTable {
       background-color: #455A64;
       color: #CFD8DC;
    }
    
    /* Sets the menu group title background colour in the header menu ONLY */
    .alfresco-share .alf-header-menu-bar .alf-menu-group.dijitMenu {
       background-color: #455A64;
    }
    
    /* Stops the line appearing between menu items in the header bar menu ONLY */
    .alfresco-share .alf-header-menu-bar .alf-menu-group .dijitReset.dijitMenuItem {
       border-bottom: none;
    }
    
    /* Dropdown menu style */
    .alfresco-share .alf-header-menu-bar .dijitMenu .dijitMenuItemHover td, .alfresco-share .alf-header-menu-bar .dijitMenu .dijitMenuItemSelected td, .alfresco-share .alf-header-menu-bar .dijitMenu .dijitMenuItemHover, .alfresco-share .alf-header-menu-bar .dijitComboBoxMenu .dijitMenuItemHover, .alfresco-share .alf-header-menu-bar .dijitMenuItemSelected{
       background-color: #455A64;
       color: #CFD8DC;
    }
    .dijitPopup.Popup .alfresco-header-AlfCascadingMenu .alf-menu-group.dijitMenu .alf-menu-group-items .alf-dropdown-menu{
       background-color: #455A64;
       color: #CFD8DC;
    
    }
    .alfresco-share .dijitPopup.Popup .alfresco-header-AlfCascadingMenu .dijitMenuItem{
       background-color: #455A64;
       color: #CFD8DC;
    }
    
    .alfresco-share .alfresco-header-AlfCascadingMenu .dijitMenu .dijitMenuItemHover td, .alfresco-share .alfresco-header-AlfCascadingMenu .dijitMenu .dijitMenuItemSelected td, .alfresco-share .alfresco-header-AlfCascadingMenu .dijitMenu .dijitMenuItemHover, .alfresco-share .alfresco-header-AlfCascadingMenu .dijitComboBoxMenu .dijitMenuItemHover, .alfresco-share .alfresco-header-AlfCascadingMenu .dijitMenuItemSelected{
       background-color: #455A64;
       color: #CFD8DC;
    }
    
    /* User status header style */
    .alfresco-header-CurrentUserStatus .status{
       background-color: #FF5722;
       color: #FFFFFF;
    }
    
    .alfresco-header-CurrentUserStatus .status.blank {
       color: #FFFFFF;
    }
    
    div#HEADER_USER_STATUS{
       -webkit-flex-shrink: 0;
       -ms-flex-negative: 0;
       flex-shrink: 0;
       overflow: hidden;
       text-align: center;
       cursor: pointer;
       margin: 10px 12px;
    }
    
    /* Responsive Header Design */
    
    /* Media Queries
    –––––––––––––––––––––––––––––––––––––––––––––––––– */
    
    /* Larger than mobile */
    @media (min-width: 400px) {}
    
    /* Larger than phablet (also point when grid becomes active) */
    @media (min-width: 550px) {}
    
    /* Larger than tablet */
    @media (min-width: 750px) {}
    
    /* Larger than desktop */
    @media (min-width: 1000px) {}
    
    /* Larger than Desktop HD */
    @media (min-width: 1200px) {}


The Material Palette colour scheme can be found in the css folder `src/main/resources/META-INF/resoures/css/palette.css`.

## Maven and artifacts

Maven filtering added to `pom.xml`:

    <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-resources-plugin</artifactId>
        <version>2.7</version>
        <dependencies>
            <dependency>
                <groupId>org.apache.maven.shared</groupId>
                <artifactId>maven-filtering</artifactId>
                <version>1.3</version>
            </dependency>
        </dependencies>
    </plugin>

# TODO

- Responsive menu
- bug fixes
- minor improvements
