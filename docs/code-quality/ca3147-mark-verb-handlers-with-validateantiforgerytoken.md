---
title: 'CA3147: Verb-Handler mit ValidateAntiForgeryToken markieren'
ms.date: 08/08/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 96660dfe1de6b4fb2490bd00b7ce408d0548ba67
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954697"
---
# <a name="ca3147-mark-verb-handlers-with-validateantiforgerytoken"></a>CA3147: Verb-Handler mit ValidateAntiForgeryToken markieren

|||
|-|-|
|TypeName|MarkVerbHandlersWithValidateAntiForgeryToken|
|CheckId|CA3147|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Eine ASP.NET MVC-Controller-Aktionsmethode ist nicht mit markiert [ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/web-frameworks/dd492108(v=vs.118)), oder ein Attribut, das Angeben der HTTP-Verb, z. B. [HttpGetAttribute](/previous-versions/aspnet/web-frameworks/ee470993(v%3dvs.118)) oder [ AcceptVerbsAttribute](/previous-versions/aspnet/web-frameworks/dd470553%28v%3dvs.118%29).

## <a name="rule-description"></a>Regelbeschreibung

Wenn Sie ASP.NET MVC-Controller zu entwerfen, achten Sie darauf, dass Sie von websiteübergreifenden anforderungsfälschungen. Ein websiteübergreifende anforderungsfälschung Angriff kann böswillige Anforderungen von einem authentifizierten Benutzer in den ASP.NET MVC-Controller senden. Weitere Informationen finden Sie unter [XSRF/CSRF-Schutz in ASP.NET MVC und Web Pages](/aspnet/mvc/overview/security/xsrfcsrf-prevention-in-aspnet-mvc-and-web-pages).

Diese Regel überprüft, ASP.NET MVC-Controller Aktionsmethoden entweder:

- Haben die [ValidateAntiforgeryTokenAttribute](/previous-versions/aspnet/web-frameworks/dd492108%28v%3dvs.118%29) , und geben Sie die zulässige HTTP-Verben, einschließlich nicht auf HTTP GET.

- Geben Sie als eine zulässige Verb HTTP GET.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

- Für ASP.NET MVC-Controlleraktionen, die HTTP GET-Anforderungen verarbeiten und keine potenziell schädliche Nebeneffekte haben, fügen eine [HttpGetAttribute](/previous-versions/aspnet/web-frameworks/ee470993%28v%3dvs.118%29) an die Methode.

   Wenn Sie eine ASP.NET MVC-Controlleraktion, die HTTP GET behandelt anfordert und potenziell schädliche Nebeneffekte, wie z. B. das Ändern von sensiblen Daten verfügen, ist Ihre Anwendung anfällig für websiteübergreifende anforderungsfälschungen.  Sie müssen Ihre Anwendung neu zu entwerfen, sodass nur HTTP POST, PUT oder DELETE-Anforderungen sensibler Vorgänge Ausführung.

- Für ASP.NET MVC-Controlleraktionen, die HTTP POST behandelt, PUT oder DELETE-Anforderungen, hinzufügen [ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/web-frameworks/dd492108(v=vs.118)) und Attributen zur Angabe von zulässigen HTTP-Verben ([AcceptVerbsAttribute](/previous-versions/aspnet/web-frameworks/dd470553%28v%3dvs.118%29) [HttpPostAttribute](/previous-versions/aspnet/web-frameworks/ee264023%28v%3dvs.118%29), [HttpPutAttribute](/previous-versions/aspnet/web-frameworks/ee470909%28v%3dvs.118%29), oder [HttpDeleteAttribute](/previous-versions/aspnet/web-frameworks/ee470917%28v%3dvs.118%29)). Darüber hinaus müssen Sie zum Aufrufen der [HtmlHelper.AntiForgeryToken()](/previous-versions/aspnet/web-frameworks/dd504812%28v%3dvs.118%29) Methode, die von Ihrem MVC-Ansicht oder Webseite Razor. Ein Beispiel finden Sie unter [Überprüfen der Edit-Methoden und die Bearbeitungsansicht](/aspnet/mvc/overview/getting-started/introduction/examining-the-edit-methods-and-edit-view).

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher, um eine Warnung dieser Regel zu unterdrücken, falls:

- Die ASP.NET MVC-Controlleraktion wurde keine schädliche Nebeneffekte.

- Die Anwendung überprüft das Antifälschungstoken auf andere Weise.

## <a name="validateantiforgerytoken-attribute-example"></a>Beispiel für ein Attribut ValidateAntiForgeryToken

### <a name="violation"></a>Verletzung

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            // You don't want an attacker to specify to who and how much money to transfer.

            return null;
        }
    }
}
```

### <a name="solution"></a>Lösung

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            return null;
        }
    }
}
```

## <a name="httpget-attribute-example"></a>Beispiel der HttpGet-Attribut

### <a name="violation"></a>Verletzung

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult Help(int topicId)
        {
            // This Help method is an example of a read-only operation with no harmful side effects.
            return null;
        }
    }
}
```

### <a name="solution"></a>Lösung

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpGet]
        public ActionResult Help(int topicId)
        {
            return null;
        }
    }
}
```
