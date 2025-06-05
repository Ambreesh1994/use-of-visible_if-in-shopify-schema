# use-of-visible_if-in-shopify-schema
Visuble_if is the latest shopify schema update 

In Shopify's schema for sections, the visible_if property allows developers to conditionally control the visibility of settings within the Theme Editor. This means a setting can be hidden or shown based on other settings' values, streamlining the user experience and preventing errors. For example, a setting related to a button's link can only be visible if another setting related to a button is enabled. 


{% schema %}
  {
    "name": "Custom-section",
    "settings": [
      {
        "type": "header",
        "content": "Media"
      },
      {
        "type": "select",
        "id":"media__type_1",
        "label": "Type",
        "options": [
          {
            "value": "image",
            "label": "Image"
          },
          {
            "value": "video",
            "label": "Video"
          }
        ],
        "default":"image"
      },
      {
        "type": "image_picker",
        "id":"image",
        "label": "Image",
        "visible_if": "{{ section.settings.media__type_1 == 'image' }}"
      },
      {
        "type": "video",
        "id":"video",
        "label": "Video",
        "visible_if": "{{ section.settings.media__type_1 == 'video' }}"
      }
    ],
    "presets": [
      {
        "name": "latest section"
      }
    ]
  }
{% endschema %}
