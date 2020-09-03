---
title: Dropdown Leiste | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7db4296a8fa4146a52d167bce3d8b051aa3ca073
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204655"
---
# <a name="drop-down-bar"></a>Dropdownleiste
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Dropdown Leiste wird am oberen Rand des Code Fensters bereitgestellt und enthält zwei Dropdown Listen.  
  
## <a name="drop-down-bar-interfaces"></a>Schnittstellen der Dropdown Leiste  
 In [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] enthält die Dropdown Leiste beispielsweise Listen für [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] Elemente und [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] Elemente Element Funktionen, wie in der folgenden Abbildung dargestellt.  
  
 ![Dropdown&#45;Dropdown leisten](../extensibility/media/vsdropdown-bar.gif "vsDropdown_bar")  
Dropdown Leiste  
  
 Beim Implementieren einer Dropdown Leiste sind vier Schnittstellen der primären Wichtigkeit vorhanden:  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implementieren Sie diese Schnittstelle, um den Inhalt der Dropdown Leiste einzufügen. Jede Dropdown-Kombination kann nur-Text oder Text (Fett, unterstrichen oder kursiv) enthalten, kann Schriftart Farben im Fenster Text enthalten und kann optional eine kleine Bitmap neben dem Dropdown Element angeben. Ähnlich wie bei der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> Schnittstelle werden Bitmap-Bilder in Bildlisten bereitgestellt. Jede Dropdown-Kombination kann eine andere Bildliste aufweisen. jede Bildliste muss jedoch Bilder derselben Höhe enthalten. Außerdem können Sie mit der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> Methode für jede Kombination eine QuickInfo bereitstellen.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Rufen Sie diese Schnittstelle auf, um die Dropdown Leiste für ein Code Fenster zu erstellen oder zu zerstören. Diese Schnittstelle kann auch verwendet werden, um zu bestimmen, ob eine Dropdown Leiste bereits an ein Code Fenster angefügt ist, indem die-Methode aufgerufen wird <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> . Ruft <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> für <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> von ab <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> .  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Diese Schnittstelle wird aufgerufen, um direkt mit der Dropdown Leiste zu kommunizieren. Sie können diese Schnittstelle verwenden, um eine Aktualisierung des Inhalts der Dropdown Leiste zu erzwingen oder die Auswahl in einem der Listenfelder zu ändern.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Wenn Sie den `ShowDropdownBarOption` in Ihrem Sprachdienst-Registrierungsschlüssel registriert haben, muss Ihr Code Fenster-Manager dieses Ereignis überwachen, um mit den Benutzereinstellungen zu synchronisieren, ob die Dropdown Leiste angezeigt werden soll. Wenn Sie diese Option nicht in Ihrem Sprachdienst Schlüssel registrieren, ist die Option zum ein-oder Ausblenden der Dropdown Leiste im Menü **Optionen** deaktiviert.  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>Anfügen einer Dropdown Leiste an ein Code Fenster  
 Um dem Code Fenster beim Erstellen eine Dropdown Leiste anzufügen, sollte ein Sprachdienst an die Dropdown Leiste angefügt werden, wenn die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> Methode aufgerufen wird. Wenn ein Aufrufe der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> -Methode anzeigt, dass noch keine Dropdown Leiste vorhanden ist, wird aufgerufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A> . Um auf die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> Schnittstelle zuzugreifen, wenden <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> Sie den- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> Zeiger an, den Sie beim <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> Anfügen der Implementierung erhalten haben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anpassen von Code Fenstern mithilfe der Legacy-API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Unterstützen der Navigationsleiste in einem Legacysprachdienst](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)
