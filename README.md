# ScrivitoAdvancedEditors

Provides some advanced Editors and details view extensions for scrivito

## Installation

Add to your gemfile

    gem 'scrivito_advanced_editors'
    gem 'font-awesome-rails'

Add this line to your application Stylesheet manifest:

    *= require scrivito_advanced_editors/styles

Add this line to your editing Stylesheet manifest:

    /= require scrivito_advanced_editors/scripts

If do not need all contained features, you can add them individually. 

## Included Editors

### Scrivito Toggle Button

A helper method that renders buttons by a given list. Click on one to toggle the content.

#### Usage

The easiest is to use the helper method.

    scrivito_toggle_button_editor(obj, attribute, list)

*If no list is given, the attribute type have to be an enum.*

A block can be set to edit the view of one button. This is usefull if used to select icons or colors.

    scrivito_toggle_button_editor(obj, attribute, list) do |text|
      scrivito_tag(:button, obj, attribute, class: 'my_css_class', style: 'some_custome_styling', data: {editor: 'scrivito-toggle-button', content: text}) do
        content_tag(:i, '', class: 'fa fa-icon') + text
      end
    end

### Slider

### List Editor

This Editor can be used to edit word lists like tags.

#### Usage

Simply specify the editor on scrivito_tag.

    scrivito_tag(:div, obj, attribute, data: {editor: 'scrivito-list-editor'})

The normal delimiter is '|'. Ich you need a different, add the data atrribute `data-delimiter`.

    scrivito_tag(:div, obj, attribute, data: {editor: 'scrivito-list-editor', delimiter: ','})

### Scrivito Textarea Editor

Use this editor if you want to edit longer text but don't want the wysiwyg editor. Example for this could be descriptions in meta datas.

#### Usage

Simply add the editor to scrivito_tag.

    scrivito_tag(:div, obj, attribute, data: {editor: 'scrivito-textarea-editior'})

## Included Extensions

### Tab View

The Tab view is to seperate your attributes if there are many at one cms object. This could be meta datas, datas for different devices or so on.
So have a better survey over your params.

#### Usage

You have to add some blocks to your details view.
Set the class `active` to the tab list to select the initial active panel.

    <ul class="tab-list">
      <li data-panel-target="#panel1" class="active">Elem1</li>
      <li data-panel-target="#panel2">Elem2</li>
    </ul>

    <div class="tab-panels">
      <div class="tab-panel" id="panel1">
        scrivito_tags for panel 1 are here ....
      </div>

      <div class="tab-panel" id="panel2">
        scrivito_tags for panel 2 are here ....
      </div>
    </div>

