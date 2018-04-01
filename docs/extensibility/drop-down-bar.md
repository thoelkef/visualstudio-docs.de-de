---
title: Dropdown-Leiste | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7058c0b93cd0ff4afb2a13b625cd7ef034b03699
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="drop-down-bar"></a>Dropdown-Leiste
Die Dropdown-Leiste wird am Anfang des Codefensters bereitgestellt und enthält zwei Dropdownlisten.  
  
## <a name="drop-down-bar-interfaces"></a>Dropdown-Leiste-Schnittstellen  
 In [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], z. B. enthält die Leiste Dropdown-Listen für [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] Elemente und [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] Memberfunktionen Elemente, wie im folgenden Bild gezeigt.  
  
 ![Drop &#45; Balken unten](../extensibility/media/vsdropdown_bar.gif "VsDropdown_bar")  
Dropdown-Leiste  
  
 Wenn Sie eine Dropdown-Leiste zu implementieren, stehen vier Schnittstellen von primärer Bedeutung:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implementieren Sie diese Schnittstelle, um den Inhalt der Dropdown-Leiste einfügen. Jede Kombination Dropdownelement darf nur-Text oder Text mit Effekten (fett, unterstrichen oder kursiv) haben Fenster Text Schriftart Färbung oder abgeblendet, Schriftarten, Farben und können optional eine kleine Bitmap neben dem Dropdown-Element bereitstellen. Ähnlich wie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> Schnittstelle Bitmapbildern in Bildlisten bereitgestellt. Jede Kombination Dropdownelement kann eine anderes Bildliste haben; Allerdings muss jeder Bildliste Bilder der gleichen Höhe enthalten. Darüber hinaus verwenden die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> Methode können Sie eine QuickInfo für jede Kombination aus bereit.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Rufen Sie diese Schnittstelle zum Erstellen oder zerstören der Dropdown-Leiste für ein Codefenster. Diese Schnittstelle kann auch verwendet werden, um festzustellen, ob eine Dropdown-Leiste bereits in einem Codefenster, durch Aufrufen zugeordnet ist der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> Methode. Rufen Sie <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> für <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> aus <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Rufen Sie diese Schnittstelle kommunizieren direkt mit dem Dropdown-Leiste. Sie können diese Schnittstelle zum Erzwingen der Aktualisierung von der Dropdown-Inhalt oder zum Ändern der Auswahl eines Listenfeldern.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Wenn Sie registriert haben die `ShowDropdownBarOption` in Ihrer Sprache Service-Registrierungsschlüssel, klicken Sie dann der Code-Fenster-Manager muss Überwachen dieses Ereignis zum Synchronisieren mit benutzereinstellungen bezüglich gibt an, ob die Dropdown-Leiste angezeigt werden soll. Wenn Sie diese Option nicht in Ihrer Sprache Dienstschlüssel registrieren, und klicken Sie dann die Option zum Anzeigen oder Ausblenden der Dropdown-Leiste ist deaktiviert, auf die **Optionen** Menü.  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>Anfügen einer Dropdown-Leiste in einem Codefenster  
 Um eine Dropdown-Leiste in das Codefenster anzufügen, bei der Erstellung, sollten fügen Sie ein Sprachdienst an der Dropdown-Leiste, wenn die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> -Methode aufgerufen wird. Wenn ein Aufruf von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> Methode gibt an, dass eine Dropdown-Leiste nicht bereits vorhanden ist und dann aufrufen, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>. Für den Zugriff auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> Schnittstelle, rufen Sie <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> aus der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> Zeiger zurückgegeben, wenn Ihre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> Implementierung wurde angefügt.  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen von Code-Fenster mit der Legacy-API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Unterstützen der Navigationsleiste in einem Legacysprachdienst](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)