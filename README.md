# Nova Extension: jQuery

This extension provides a helper for writing jQuery selectors. It's intended as a utility for extension writers and does not provide any changes to Nova on its own.

An an example, is used by the [chronological_mission_posts](https://github.com/jonmatterson/nova-ext-chronological_mission_posts) extension like this:

```
$this->event->listen(['location', 'view', 'output', 'admin', 'manage_posts_edit'], function($event){

  $event['output'] .= $this->extension['jquery']['generator']
                  ->select('[name="post_timeline"]')->closest('p')
                  ->after(
                    $this->extension['chronological_mission_posts']
                         ->view('write_missionpost', $this->skin, 'admin', $event['data'])
                  );

  $event['output'] .= $this->extension['jquery']['generator']
                           ->select('[name="post_timeline"]')->closest('p')->remove();
                  
});
```

This extension currently supports the following chained methods: `first`, `last`, `before`, `after`, `append`, `prepend`, `html`, `text`, `closest`, and `remove`. Submit a pull request for additional methods.

## Requirements

This extension requires:

- Nova 2.6+

## Installation

Copy the entire directory into `applications/extensions/jquery`.

Add the following to `application/config/extensions.php`:

```
$config['extensions']['enabled'][] = 'jquery';
```
