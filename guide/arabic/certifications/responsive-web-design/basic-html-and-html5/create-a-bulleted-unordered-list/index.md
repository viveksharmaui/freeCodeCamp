---
title: Create a Bulleted Unordered List
localeTitle: قم بإنشاء قائمة غير مرتبة بالعدادات
---
## قم بإنشاء قائمة غير مرتبة بالعدادات

لتمرير التحدي ، فإن أول عملية يجب عليك القيام بها هي إزالة عناصر `p` بكل محتواها.

بعد أن لديك لتنفيذ قائمة: يجب أن يحتوي على ثلاثة على الأقل `li` عنصر داخل `ul` عنصر وهذه `li` يجب أن يكون على نفس المستوى، وليس متداخلة في بعضها البعض:

صيح:

```
<ul>
  <li></li>
  <li></li>
</ul>
``` 

غير صحيح:

```
<ul>
  <li>
    <li>
    </li>
  </li>
</ul>
``` 

حظا طيبا وفقك الله!