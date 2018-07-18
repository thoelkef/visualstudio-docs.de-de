---
title: Abrufen von Informationen zur Schriftart und Farbe für Text farbliche Kennzeichnung | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8c86e37d6d7da9da0a6b0978770bf7d7564fa19c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129695"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Abrufen von Informationen zur Schriftart und Farbe für die farbliche Kennzeichnung von Text
Der Prozess, der gerendert wird, oder zeigt Farbdruckoption Text in die Elemente der Benutzeroberfläche (UI) hängt vom Typ von Projekt, dessen Technologie und Developer-Einstellungen. Die **Schriftarten und Farben** Eigenschaftenseite speichert die Einstellungen.

 Die meisten Implementierungen, die Farbdruckoption Text anzeigen müssen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> und die zugehörigen Schnittstellen für vorlegen, abrufen und Speichern von Text Einstellungen anzuzeigen.

> [!NOTE]
>  Wenn die Core-Editor anpassen (welche unterstützt die **Text EditorCategory**), es wird empfohlen, dass Sie der Sprachdienst die Färbung-Technologie verwenden. Weitere Informationen finden Sie unter [Schriftart und Farbe (Übersicht)](../extensibility/font-and-color-overview.md).

## <a name="getting-default-font-and-color-information"></a>Abrufen von Standardschriftart und Farbinformationen
 Alle der **Schriftarten und Farben** Einstellungen von einem beliebigen Fenster, das Anzeigen von Text sollte angegeben werden, der **Anzeigeelementen** einer **Kategorie**. Weitere Informationen finden Sie unter [Schriftarten und Farben, Umgebung, Optionen (Dialogfeld)](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).

Um die zur farblichen Kennzeichnung, benötigen eine VSPackage aktuellen **Schriftarten und Farben** Einstellungen. Eine VSPackage kann die folgenden Möglichkeiten, je nachdem muss die aktuelle Einstellungen abrufen:

-   Verwenden Sie die Dauerhaftigkeit von Schriftart und Farbe beim Abrufen des gespeicherten oder der aktuellen Status an. Weitere Informationen finden Sie unter [Zugriff auf gespeicherte Schriftart und Farbe Einstellungen](../extensibility/accessing-stored-font-and-color-settings.md).

-   Verwenden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> Schnittstelle eines Diensts, die Schriftart und Farbe Daten zum Abrufen einer Instanz des bereitstellt <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, wenn das VSPackage nicht gleichzeitig die Schriftart und Farbe Anbieter fungiert.

-   Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>-Schnittstelle.

Um sicherzustellen, dass durch Abruf erzielten Ergebnisse sind auf dem neuesten Stand, es kann hilfreich sein, verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> Schnittstelle, um zu bestimmen, ob ein Update erforderlich ist, vor dem Aufrufen der Abrufmethoden, der die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle.

Nachdem abgerufen Sie Schriftart und Farbe Informationen wurden, analysieren Sie den Text angezeigt werden, um Elemente zu identifizieren, die farbliche Kennzeichnung erfordern. Zeigt den Text im Fenster mit der entsprechenden Schriftarten und Farben.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- [Verwenden von Schriftarten und Text](/dotnet/framework/winforms/advanced/using-fonts-and-text)
- [Arbeiten mit Farben](/cpp/windows/working-with-color-image-editor-for-icons)
- [GDI (Graphics Device Interface)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)