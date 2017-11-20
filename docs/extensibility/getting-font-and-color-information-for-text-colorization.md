---
title: "Abrufen von Informationen zur Schriftart und Farbe für Text farbliche Kennzeichnung | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e3b31ad2ec080070dec3c68b304f400d204d47a0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Abrufen von Informationen zur Schriftart und Farbe für die farbliche Kennzeichnung von Text
Der Prozess, der gerendert wird, oder zeigt Farbdruckoption Text in die Elemente der Benutzeroberfläche (UI) hängt vom Typ von Projekt, dessen Technologie und Developer-Einstellungen. Die **Schriftarten und Farben** Eigenschaftenseite speichert die Einstellungen.  
  
 Die meisten Implementierungen, die Farbdruckoption Text anzeigen müssen die `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` und die zugehörigen Schnittstellen für vorlegen, abrufen und Speichern von Text Einstellungen anzuzeigen.  
  
> [!NOTE]
>  Wenn die Core-Editor anpassen (welche unterstützt die **Text EditorCategory**), es wird dringend empfohlen, dass Sie der Sprachdienst die Färbung-Technologie verwenden. Weitere Informationen finden Sie unter [Schriftart und Farbe (Übersicht)](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Abrufen von Standardschriftart und Farbinformationen  
 Alle der **Schriftarten und Farben** Einstellungen von einem beliebigen Fenster, das Anzeigen von Text sollte angegeben werden, der **Anzeigeelementen** einer **Kategorie**. Weitere Informationen finden Sie unter [Schriftarten und Farben, Umgebung, Optionen (Dialogfeld)](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Um die zur farblichen Kennzeichnung, benötigen eine VSPackage aktuellen **Schriftarten und Farben** Einstellungen. Eine VSPackage kann dies auf folgende Weise, abhängig von der Anforderungen zu erreichen:  
  
-   Verwenden Sie die Dauerhaftigkeit von Schriftart und Farbe beim Abrufen des gespeicherten oder der aktuellen Status an. Weitere Informationen finden Sie unter [Zugriff auf gespeicherte Schriftart und Farbe Einstellungen](../extensibility/accessing-stored-font-and-color-settings.md).  
  
-   Verwenden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> Schnittstelle eines Diensts Bereitstellen von Schriftart und Farbe Daten zum Abrufen einer Instanz des <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, wenn das VSPackage nicht gleichzeitig die Schriftart und Farbe Anbieter fungiert.  
  
-   Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>-Schnittstelle.  
  
 Um sicherzustellen, dass durch Abruf erzielten Ergebnisse sind auf dem neuesten Stand, es kann hilfreich sein, verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> Schnittstelle, um zu bestimmen, ob ein Update erforderlich ist, vor dem Aufrufen der Abrufmethoden, der die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle.  
  
 Nachdem Sie Schriftart und Farbe Informationen abgerufen wurden, analysieren Sie den Text, der zum Identifizieren von Elementen, die farbliche Kennzeichnung erfordern angezeigt werden, und klicken Sie dann den Text im Fenster mit der entsprechenden Schriftarten und Farben angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Verwenden von Schriftarten und Text](/dotnet/framework/winforms/advanced/using-fonts-and-text)   
 [Arbeiten mit Farben](/cpp/windows/working-with-color-image-editor-for-icons)   
 [GDI (Graphics Device Interface)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)