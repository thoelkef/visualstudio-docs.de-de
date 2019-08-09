---
title: Schreiben und Debuggen von XAML mithilfe von XAML Hot Neuladen
description: XAML Hot Neuladen oder XAML-bearbeiten und Fortfahren ermöglicht es Ihnen, während der Ausführung von apps Änderungen an Ihrem XAML-Code vorzunehmen.
ms.date: 08/05/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0acacac883153990861385c96eeb3379c464f97f
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68870992"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Schreiben und Debuggen von XAML-Code mit XAML-Hot-Neuladen in Visual Studio

Das heiße Laden von XAML unterstützt Sie beim Erstellen der Benutzeroberfläche der WPF-oder UWP-APP, indem Sie Änderungen an XAML-Code vornehmen können, während Ihre APP ausgeführt wird. Hot-Neuladen ist sowohl in Visual Studio als auch in Blend für Visual Studio verfügbar. Mit dieser Funktion können Sie XAML-Code inkrementell erstellen und testen, indem Sie den Datenkontext der ausgelaufenden APP, den Authentifizierungs Status und eine andere reale Komplexität, die während der Entwurfszeit schwer zu simulieren ist, nutzen.

Das erneute Laden von XAML ist besonders in den folgenden Szenarien hilfreich:

* Behebung von Benutzeroberflächen Problemen in Ihrem XAML-Code, nachdem die APP im Debugmodus gestartet wurde.

* Die Entwicklung einer neuen Benutzeroberflächen Komponente für eine APP, die sich in der Entwicklung befindet, während der Lauf Zeit Kontext ihrer App genutzt wird.

|Unterstützte Anwendungs Typen|Betriebssystem und Tools|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6+</br>Windows 7 und höher |
|Universelle Windows-Apps (UWP)|Windows 10 und höher mit dem [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

> [!NOTE]
> Das Laden von Visual Studio XAML Hot wird zurzeit nur unterstützt, wenn Sie die Anwendung in Visual Studio ausführen oder Blend für Visual Studio mit angefügtem Debugger (**F5** oder **Debuggen starten**). Sie können diese Funktion nicht aktivieren, indem Sie [an den Prozess anhängen](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)verwenden.

## <a name="known-limitations"></a>Bekannte Einschränkungen

Im folgenden finden Sie bekannte Einschränkungen für das heiße Laden von XAML. Beenden Sie den Debugger, und schließen Sie den Vorgang ab, um die Einschränkung zu umgehen, die Sie in ausführen.

|Einschränkung|WPF|UWP|Hinweise|
|-|-|-|-|
|Verknüpfen von Ereignissen mit Steuerelementen während der Ausführung der APP|Nicht unterstützt|Nicht unterstützt|Siehe Fehler: *Fehler bei Fehler*|
|Erstellen von Ressourcen Objekten in einem Ressourcen Wörterbuch, z. b. in der Seite/im Fenster der APP oder in der *app. XAML*|Nicht unterstützt|Unterstützt|Beispiel: Hinzufügen `SolidColorBrush` eines zu einem Ressourcen Wörterbuch, `StaticResource`das als verwendet werden soll.</br>Hinweis: Statische Ressourcen, Format Konverter und andere in ein Ressourcen Wörterbuch geschriebene Elemente können beim Verwenden von XAML-Hot-Neuladen angewendet/verwendet werden. Nur die Erstellung der Ressource wird nicht unterstützt.</br> Ändern der Eigenschaft des `Source` Ressourcen Wörterbuchs.|
|Hinzufügen von neuen Steuerelementen, Klassen, Fenstern oder anderen Dateien zu Ihrem Projekt, während die app ausgeführt wird|Nicht unterstützt|Nicht unterstützt|None|
|Verwalten von nuget-Paketen (hinzufügen/entfernen/aktualisieren von Paketen)|Nicht unterstützt|Nicht unterstützt|None|
|Ändern der Datenbindung, die die {x:Bind}-Markup Erweiterung verwendet|N/V|In Visual Studio 2019 und höheren Versionen unterstützt|Wird in Visual Studio 2017 oder früheren Versionen nicht unterstützt.|

## <a name="error-messages"></a>Fehlermeldungen

Bei der Verwendung von XAML Hot Neuladen treten möglicherweise die folgenden Fehler auf.

|Fehlermeldung|Beschreibung|
|-|-|
|Fehler bei Fehler|Der Fehler gibt an, dass Sie versuchen, ein Ereignis an eines der Steuerelemente zu übertragen, was nicht unterstützt wird, während die Anwendung ausgeführt wird.|
|Die XAML-Funktion „Bearbeiten und Fortfahren“ hat keine Elemente für die Aktualisierung gefunden.|Der Fehler tritt auf, wenn Sie XAML bearbeiten, dass das heiße laden in Ihrer APP nicht aktualisiert werden kann.</br> Dieser Fehler kann manchmal behoben werden, indem Sie Ihre laufende App verwenden, um zu einer Ansicht zu navigieren, in der der XAML-Code verwendet wird.</br> In manchen Fällen bedeutet dieser Fehler, dass die jeweilige Änderung nicht angewendet werden kann, bis Sie die Debugsitzung neu starten. |
|Diese Änderung wird während einer Debugsitzung nicht unterstützt.|Der Fehler gibt an, dass die Änderung, die Sie versuchen, von XAML Hot Neuladen nicht unterstützt wird. Nehmen Sie die Debugsitzung an, nehmen Sie die Änderung vor, und starten Sie die Debugsitzung neu.|
