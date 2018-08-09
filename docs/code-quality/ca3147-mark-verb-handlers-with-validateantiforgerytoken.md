---
title: 'CA3147: Markieren Sie Verb-Handler mit ValidateAntiForgeryToken'
ms.date: 08/08/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 4b4369cfd310be9322d17b8bdbfe79880f2aa579
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008702"
---
# <a name="ca3147-mark-verb-handlers-with-validateantiforgerytoken"></a>CA3147: Markieren Sie Verb-Handler mit ValidateAntiForgeryToken

|||
|-|-|
|TypeName|MarkVerbHandlersWithValidateAntiForgeryToken|
|CheckId|CA3147|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Eine ASP.NET MVC-Controller-Aktionsmethode ist nicht mit markiert <xref:Microsoft.AspNetCore.Mvc.ValidateAntiForgeryTokenAttribute?displayProperty=fullName>, oder ein Attribut, das Angeben der HTTP-Verb, z. B. <xref:Microsoft.AspNetCore.Mvc.HttpGetAttribute?displayProperty=fullName> oder <xref:Microsoft.AspNetCore.Mvc.AcceptVerbsAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung

Wenn Sie ASP.NET MVC-Controller zu entwerfen, achten Sie darauf, dass Sie von websiteübergreifenden anforderungsfälschungen. Ein websiteübergreifende anforderungsfälschung Angriff kann böswillige Anforderungen von einem authentifizierten Benutzer in den ASP.NET MVC-Controller senden. Weitere Informationen finden Sie unter [XSRF/CSRF-Schutz in ASP.NET MVC und Web Pages](/aspnet/mvc/overview/security/xsrfcsrf-prevention-in-aspnet-mvc-and-web-pages).

Diese Regel überprüft, ASP.NET MVC-Controller Aktionsmethoden entweder:

- Haben die <xref:Microsoft.AspNetCore.Mvc.ValidateAntiForgeryTokenAttribute> , und geben Sie die zulässige HTTP-Verben, einschließlich nicht auf HTTP GET.

- Geben Sie als eine zulässige Verb HTTP GET.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

- Für ASP.NET MVC-Controlleraktionen, die HTTP GET-Anforderungen verarbeiten und keine potenziell schädliche Nebeneffekte haben, fügen eine <xref:Microsoft.AspNetCore.Mvc.HttpGetAttribute> an die Methode.

   Wenn Sie eine ASP.NET MVC-Controlleraktion, die HTTP GET behandelt anfordert und potenziell schädliche Nebeneffekte, wie z. B. das Ändern von sensiblen Daten verfügen, ist Ihre Anwendung anfällig für websiteübergreifende anforderungsfälschungen.  Sie müssen Ihre Anwendung neu zu entwerfen, sodass nur HTTP POST, PUT oder DELETE-Anforderungen sensibler Vorgänge Ausführung.

- Für ASP.NET MVC-Controlleraktionen, die HTTP POST behandelt, PUT oder DELETE-Anforderungen, hinzufügen <xref:Microsoft.AspNetCore.Mvc.ValidateAntiForgeryTokenAttribute> und Attributen zur Angabe von zulässigen HTTP-Verben (<xref:Microsoft.AspNetCore.Mvc.AcceptVerbsAttribute>, <xref:Microsoft.AspNetCore.Mvc.HttpPostAttribute>, <xref:Microsoft.AspNetCore.Mvc.HttpPutAttribute>, oder <xref:Microsoft.AspNetCore.Mvc.HttpDeleteAttribute>). Darüber hinaus müssen Sie zum Aufrufen <xref:Microsoft.AspNetCore.Mvc.ViewFeatures.HtmlHelper.AntiForgeryToken%2A?displayProperty=nameWithType> von Ihrem MVC-Ansicht oder Webseite Razor. Ein Beispiel finden Sie unter [Überprüfen der Edit-Methoden und die Bearbeitungsansicht](/aspnet/mvc/overview/getting-started/introduction/examining-the-edit-methods-and-edit-view).

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
