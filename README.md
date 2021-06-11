# Entity attributes

Entity attributes allows you to show basic attributes from multiple entities.

![enitty-attributes-card](https://user-images.githubusercontent.com/7738048/42527876-8e9f1206-8482-11e8-9e19-b5ffbfbf8474.png)

**Options**

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| type | string | **Required** | `custom:entity-attributes-card`
| title | string | optional | A title for the card
| heading_name | string | 'Attributes' | Heading of the attribute column
| heading_state | string | 'States' | Heading of the states column
| filter | object | **Required** | A filter object that can contain `include` and `exclude` sections

⚠️ `include` and `exclude` can be simple lists (format `[domain]`.`[entity]`.`[attribute]`) or objects of type below. `[attribute]` can also be a pattern.

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| key | string | **Required** | A pattern for the attribute. Example: `media_player.bedroom.media_title`
| name | string | optional | A string to replace the actual attribute name with
| unit | string | optional | A string to append an arbitrary unit to the value

**Example**

```yaml
entity: sun.sun
filter:
  include:
    - sun.sun.next_rising
    - sun.sun.next_setting
    - sun.sun.next_dawn
    - sun.sun.next_dusk
type: custom:entity-attributes-card
heading_name: Name
heading_state: State
```

How to embed this inside `entities` card:

![screen shot 2018-07-09 at 13 47 38](https://user-images.githubusercontent.com/7738048/42446481-1ac27c1e-837f-11e8-94e7-02ef35f2d853.png)

```yaml
- type: entities
  title: Entities card
  entities:
    - media_player.bedroom
    - type: custom:entity-attributes-card
      entity: media_player.bedroom
      filter:
        include:
          - media_player.bedroom.app_name
          - media_player.bedroom.media_title
    - sensor.short_name
    - sensor.battery_sensor
```
