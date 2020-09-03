---
title: Erhalten von Schriftart-und Farbinformationen für die farbliche Farbgebung von Text | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8724c31accb26e478c2726dfe791256994fc95ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696858"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Abrufen von Informationen zur Schriftart und Farbe für die farbliche Kennzeichnung von Text
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Prozess, der farbige Text in Benutzeroberflächen Elementen rendert oder anzeigt, hängt vom Projekttyp, seiner Technologie und den Entwicklereinstellungen ab. Die Eigenschaften Seite **Schriftarten und Farben** speichert die Einstellungen.  
  
 Die meisten Implementierungen, die farbige Text anzeigen, benötigen die `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` und zugeordneten Schnittstellen zum darstellen, abrufen und Speichern von Textanzeige Einstellungen.  
  
> [!NOTE]
> Wenn Sie den Kern-Editor anpassen (der die **Text-EditorCategory**unterstützt), wird dringend empfohlen, die Farb Technologie im Sprachdienst zu verwenden. Weitere Informationen finden Sie unter [Übersicht über Schriftart und Farben](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Standard Schriftart-und Farbinformationen werden erhalten.  
 Alle Einstellungen für **Schriftarten und Farben** eines beliebigen Fensters, in dem Text angezeigt wird, sollten in den **Anzeigeelementen** einer **Kategorie**angegeben werden. Weitere Informationen finden Sie unter [Schriftarten und Farben, Umgebung, Dialog Feld "Optionen](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)".  
  
 Zur Farbgebung muss ein VSPackage die aktuellen **Schriftarten und Farben** abrufen. Ein VSPackage kann dies je nach Anforderungen auf folgende Weise erreichen:  
  
- Verwenden Sie den Mechanismus für die Schriftart-und Farb Persistenz, um den gespeicherten oder aktuellen Zustand abzurufen. Weitere Informationen finden Sie unter [zugreifen auf gespeicherte Schriftart-und Farbeinstellungen](../extensibility/accessing-stored-font-and-color-settings.md).  
  
- Verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> -Schnittstelle eines Dienstanbieters, der Schriftart und Farbdaten bereitstellt, um eine Instanz von zu erhalten <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> , wenn das VSPackage nicht gleichzeitig der Schriftart-und Farb Anbieter ist  
  
- Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>-Schnittstelle.  
  
  Um sicherzustellen, dass die vom Abruf abzurufenden Ergebnisse auf dem neuesten Stand sind, kann es hilfreich sein, die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> Schnittstelle zu verwenden, um zu bestimmen, ob ein Update erforderlich ist, bevor die Abruf Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle aufgerufen werden.  
  
  Nachdem Sie Schriftart-und Farbinformationen abgerufen haben, analysieren Sie den anzuzeigenden Text, um Elemente zu identifizieren, die farbige Farbgebung erfordern, und zeigen Sie dann den Text im Fenster mit den entsprechenden Schriftarten und Farben an.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Verwenden von Schriftarten und Text](https://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Arbeiten mit Farben](https://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI (Grafikgeräte Schnittstelle)](https://msdn.microsoft.com/7e1d4540-bb2e-4257-8eee-eee376acba83)
