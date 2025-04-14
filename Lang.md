# Lang

This package provides a utility function`TXT`for RN application to support localization consistent with the rest of the SeaTalk app. As SeaTalk itself is a multi-lingual platform, it's very important for RN applications being published on the SeaTalk platform to support this as well if your target users could be using different languages.

## function buildTXT

### Function

```javascript
function buildTXT(store: LocalizationStore) => TXTFunc Copy
```

### Parameters

|Name|Type|Description|
|---|---|---|
|store|LocalizationStore|The store from which the translation comes. See below.|

## interface LocalizationStore

### **Properties**

|Name|Type|Description|
|---|---|---|
|primary|LanguageCode|Primary language code to fallback to when translation is not available.|
|store|\[LanguageCode: \[string: string\]\]|A two-fold map storing all translations for all keys. It's not necessary to have translations for all the language codes supported by SeaTalk. However, you will need to ensure that the primary language is always supported. Note : If a language is not found, it will fallback to the primary language. If a key is not found in either the current displayed language or the primary language, the raw key string will be displayed.|

## Recommended Usage

This section illustrates how to use this package.For maintainability, you are strongly advised to separate your translations for different languages into different JSON files and then import them in the`LocalizationStore`.

```javascript
// Consider having such a TXT file initialisation for your whole project.const i18nStore: LocalizationStore = {
primary: 'en',
    store: {
    en: require('path/to/json/en.json'),
        'zh-hans': require('path/to/json/zh-hans.json'),
            vi: require('path/to/json/vi.json'),
    },
    };

export const TXT = buildTXT(i18nStore);

// Actual place using it (likely in a component's render function)class MyComponent extends BaseComponent {
// ...
render() {
    return <Text>{TXT('label_button')}</Text>;
}
    }

// Parametric. This works with arbitrary number of arguments.var store = { duration_text: '{0} hour {1} minutes' };
var text = TXT('duration_text', '2', '3'); // "2 hour 3 minutes" Copy
```

Was this document helpful?

No

Yes