---
title: Abrufen von Informationen zur Schriftart und Farbe für die farbliche Kennzeichnung von Text | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 49a787dd67691c581383713a7c98a80816762599
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832718"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Abrufen von Informationen zur Schriftart und Farbe für die farbliche Kennzeichnung von Text
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Prozess, der gerendert wird, oder zeigt farbige Text in die Elemente der Benutzeroberfläche (UI) hängt von den Typ des Projekts, die Technologie und Developer-Einstellungen. Die **Schriftarten und Farben** auf der Seite werden die Einstellungen gespeichert.  
  
 Die meisten Implementierungen, die farbige Text anzeigen müssen die `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` und die zugehörigen Schnittstellen, für die darstellen, abgerufen und das Speichern von Text Einstellungen anzuzeigen.  
  
> [!NOTE]
>  Beim Anpassen der Kern-Editor (welche unterstützt die **Text EditorCategory**), es wird dringend empfohlen, die Farbgebung-Technologie in den Sprachdienst zu verwenden. Weitere Informationen finden Sie unter [Schriftart und Farbe (Übersicht)](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Abrufen von Standardschriftart und Farbinformationen  
 Alle der **Schriftarten und Farben** Einstellungen von einem beliebigen Fenster, das Anzeigen von Text sollte angegeben werden, der **Anzeigeelemente** eines **Kategorie**. Weitere Informationen finden Sie unter [Schriftarten und Farben, Umgebung, Dialogfeld Optionen](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Eine VSPackage benötigen zum farbigen Anzeigen von, aktuelle **Schriftarten und Farben** Einstellungen. Eine VSPackage kann dies gibt folgende Möglichkeiten, nach Bedarf zu erreichen:  
  
- Verwenden Sie den Schriftart- und farbeinstellungen Dauerhaftigkeitsmechanismus zum Abrufen des gespeicherten oder der aktuellen Status. Weitere Informationen finden Sie unter [den Zugriff auf gespeicherte Schriftart- und Farbeinstellungen](../extensibility/accessing-stored-font-and-color-settings.md).  
  
- Verwenden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> Benutzeroberfläche eines Diensts Bereitstellen von Schriftart- und farbeinstellungen Daten zum Abrufen einer Instanz von <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, wenn das VSPackage auch nicht den Schriftart- und farbeinstellungen-Anbieter ist.  
  
- Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>-Schnittstelle.  
  
  Um sicherzustellen, dass die Ergebnisse der Abfrage werden auf dem neuesten Stand, es kann hilfreich sein, verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> Schnittstelle, um zu bestimmen, ob ein Update erforderlich ist, vor dem Aufrufen der Abrufmethoden, der die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle.  
  
  Nachdem Sie Schriftart und Farbinformationen abgerufen haben, Analysieren des Texts, der angezeigt werden, um das Identifizieren von Elementen, die farbliche Kennzeichnung erfordern, und klicken Sie dann den Text in dem Fenster mithilfe der entsprechenden Schriftarten und Farben anzeigen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Verwenden von Schriftarten und Text](http://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Arbeiten mit Farben](http://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI (Graphics Device Interface)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)

