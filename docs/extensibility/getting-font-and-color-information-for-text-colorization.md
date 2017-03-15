---
title: "Abrufen von Schriftart und Farbe Informationen für die farbliche Kennzeichnung Text | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: d0b3d50ab2a78bf806be8c7339bb260746e1c457
ms.lasthandoff: 02/22/2017

---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Schriftart und Farbe Informationen für die farbliche Kennzeichnung Text abrufen
Der Prozess, der gerendert oder Farbdruckoption Text anzeigt, in der Elemente der Benutzeroberfläche (UI) hängt vom Typ Projekt, dessen Technologie und Developer-Voreinstellungen. Die **Schriftarten und Farben** Eigenschaftenseite speichert die Einstellungen.  
  
 Die meisten Implementierungen, die Farbdruckoption Text anzeigen müssen die `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` und die zugehörigen Schnittstellen darstellen, abrufen und Speichern von Text Einstellungen anzeigen.  
  
> [!NOTE]
>  Beim Anpassen des Core-Editors (unterstützt die **Text EditorCategory**), wird empfohlen, dass Sie die Farben für Technologie in der Sprachdienst verwenden. Weitere Informationen finden Sie unter [Schriftart und Farbe (Übersicht)](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Erste Standardschriftart und die Farbinformationen  
 Alle der **Schriftarten und Farben** Einstellungen von einem beliebigen Fenster, das Anzeigen von Text sollte angegeben werden, der **Anzeigeelemente** einer **Kategorie**. Weitere Informationen finden Sie unter [Schriftarten und Farben, Umgebung, Optionen (Dialogfeld)](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Um zur farblichen Kennzeichnung, benötigen ein VSPackage aktuelle **Schriftarten und Farben** Einstellungen. Ein VSPackage erreichen dies auf folgende Weise, je nach den Anforderungen:  
  
-   Verwenden Sie beim Abrufen des gespeicherten oder der aktuellen Status die Dauerhaftigkeit von Schriftart und Farbe. Weitere Informationen finden Sie unter [Zugriff auf gespeicherte Schriftart und Farbe Einstellungen](../extensibility/accessing-stored-font-and-color-settings.md).  
  
-   Verwenden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>Schnittstelle eines Diensts Bereitstellen von Schriftart und Farbe Daten zum Abrufen einer Instanz von <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, wenn das VSPackage nicht auch die Schriftart und Farbe Anbieter.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
  
-   Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>Schnittstelle.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
  
 Um sicherzustellen, dass die Ergebnisse der Abfrage auf dem aktuellen Stand sind, es kann hilfreich sein, verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>Schnittstelle, um zu bestimmen, ob ein Update erforderlich ist, vor dem Aufrufen der Abrufmethoden, der die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>Schnittstelle.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
  
 Nachdem Sie Schriftart und Farbe Informationen abgerufen haben, analysieren Sie den Text zum Identifizieren von Elementen, die farbliche Kennzeichnung erfordern angezeigt werden, und zeigt dann den Text in das Fenster mit den entsprechenden Schriftarten und Farben.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Verwenden von Schriftarten und Text](http://msdn.microsoft.com/Library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Arbeiten mit Farben](/visual-cpp/windows/working-with-color-image-editor-for-icons)   
 [GDI (Graphics Device Interface)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)
