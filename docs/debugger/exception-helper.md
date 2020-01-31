---
title: 'Untersuchen einer Ausnahme: Visual Studio | Microsoft-Dokumentation'
ms.date: 1/18/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- exception helper, debugger, exception
- debugging [Visual Studio], exception helper, Examine an exception
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2dae1609486ec4f3462be89b0526467dd7414647
ms.sourcegitcommit: 8cbced0fb46959a3a2494852df1e41db1177a26c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2020
ms.locfileid: "76829756"
---
# <a name="inspect-an-exception-using-the-exception-helper"></a>Untersuchen einer Ausnahme mithilfe des Exception-Hilfsprogramms 

Der Umgang mit Ausnahmen ist ein häufiges Problem, unabhängig von ihrer Technologie oder ihrer Kenntnis. Es kann frustrierend sein, herauszufinden, warum Ausnahmen in Ihrem Code Probleme verursachen. Wenn Sie eine Ausnahme in Visual Studio debuggen, sollten Sie diese Frustration verringern, indem Sie Ihnen relevante Ausnahme Informationen bereitstellen, die Ihnen helfen, das Problem schneller zu debuggen.

![Ausnahmen-Hilfe](media/debugger-exception-helper-default.png)

## <a name="pause-on-the-exception"></a>Anhalten bei der Ausnahme
Wenn der Debugger bei einer Ausnahme unterbrochen wird, wird rechts neben der Codezeile ein Ausnahme Fehler Symbol angezeigt. Ein nicht modales Exception-Hilfsprogramm wird in der Nähe des Ausnahme Symbols angezeigt.

![Ausnahme-Hilfsobjekt neben einer Codezeile](media/debugger-exception-helper-locerror.png)

## <a name="inspect-exception-info"></a>Ausnahme Informationen überprüfen
Sie können den Ausnahmetyp und die Ausnahme Meldung sofort im Ausnahmen-Hilfsprogramm lesen und unabhängig davon, ob die Ausnahme ausgelöst oder nicht behandelt wurde. Sie können die Eigenschaften des Ausnahme Objekts überprüfen und anzeigen, indem Sie auf den Link **Details anzeigen** klicken.

## <a name="analyze-null-references"></a>Analysieren von Null-verweisen
Ab Visual Studio 2017 sehen Sie für .net und C/C++ Code, wenn Sie eine `NullReferenceException` oder eine `AccessViolation`erreichen, NULL-Analyse Informationen im Ausnahme-Hilfsprogramm. Die Analyse wird als Text unterhalb der Ausnahme Meldung angezeigt. In der Abbildung unten werden die Informationen als "**s** war NULL" angezeigt.

![Exception Helper-NULL-Analyse](media/debugger-exception-helper-default.png)


> [!NOTE]
> Die NULL-Verweis Analyse in verwaltetem Code erfordert die .NET-Version 4.6.2. Die NULL-Analyse wird derzeit für universelle Windows-Plattform (UWP) und andere .net Core-Anwendungen nicht unterstützt. Sie ist nur beim Debuggen von Code verfügbar, der keine Just-in-time (JIT)-Code Optimierungen enthält.

## <a name="configure-exception-settings"></a>Konfigurieren von Ausnahme Einstellungen 
Sie können den Debugger so konfigurieren, dass er nicht mehr ausgeführt wird, wenn eine Ausnahme des aktuellen Typs im **Ausnahme Einstellungs** Abschnitt der Ausnahme Unterstützung ausgelöst wird. Wenn der Debugger bei einer ausgelösten Ausnahme angehalten wird, können Sie das Kontrollkästchen verwenden, um das unterbrechen für diesen Ausnahmetyp zu deaktivieren, wenn er in der Zukunft ausgelöst wird. Wenn Sie diese spezielle Ausnahme nicht unterbrechen möchten, wenn Sie in diesem bestimmten Modul ausgelöst wird, aktivieren Sie das Kontrollkästchen im Fenster " **Ausnahme Einstellungen** " im Fenster "Ausnahme Einstellungen **" unter dem** Namen des Moduls. 

## <a name="inspect-inner-exceptions"></a>Überprüfen von inneren Ausnahmen 
Wenn die Ausnahme irgendwelche inneren Ausnahmen aufweist ([InnerException](https://docs.microsoft.com/dotnet/api/system.exception.innerexception)), können Sie Sie in der Ausnahme-Hilfsmethode anzeigen. Wenn mehrere Ausnahmen vorhanden sind, können Sie zwischen diesen mithilfe der Pfeile nach links und rechts navigieren, die oberhalb der-aufrufsstapel angezeigt werden.

![Exception-Hilfsprogramm mit innerer Ausnahme](media/debugger-exception-helper-innerexception.png)

## <a name="inspect-rethrown-exceptions"></a>Erneut ausgelöste Ausnahmen überprüfen
In Fällen, in denen eine Ausnahme `thrown` wurde, zeigt die Ausnahme-Hilfe die Aufruf Stapel an, wenn die Ausnahme zum ersten Mal ausgelöst wurde. Wenn die Ausnahme mehrmals ausgelöst wurde, wird nur die aufrufsstapel der ursprünglichen Ausnahme angezeigt.

![Exception-Hilfsprogramm mit erneut ausgelösten Ausnahmen](media/debugger-exception-helper-innerexception.png)

## <a name="share-a-debug-session-with-live-share"></a>Freigeben einer Debugsitzung mit Live Share
Aus dem Ausnahmen-Hilfsprogramm können Sie eine [Live Share](https://docs.microsoft.com/visualstudio/liveshare/) Sitzung starten, indem Sie den Link **Live Share Sitzung starten...** . Jeder Benutzer, der die Live Share Sitzung einrichtet, kann das Exception-Hilfsprogramm zusammen mit allen anderen Debuginformationen sehen.
