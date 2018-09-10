---
title: Dropdownleiste | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 030ee092909c7faa519c68ac9800d051a96f6b42
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636927"
---
# <a name="drop-down-bar"></a>Dropdownleiste
Die Dropdownleiste ist am Anfang des Codefensters und enthält zwei Dropdownlisten.  
  
## <a name="drop-down-bar-interfaces"></a>Dropdownleiste-Schnittstellen  
 In [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], z. B. die Dropdownleiste enthält Listen für [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] Elemente und [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] Elemente-Member-Funktionen, wie in der folgenden Abbildung dargestellt.  
  
 ![Drop&#45;nach-unten-Balken](../extensibility/media/vsdropdown_bar.gif "VsDropdown_bar")  
Dropdownleiste  
  
 Wenn Sie eine Dropdownleiste implementieren zu können, stehen vier Schnittstellen von primärer Bedeutung:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implementieren Sie diese Schnittstelle, um den Inhalt der Dropdownleiste einfügen. Jede Dropdown-Kombination darf nur-Text oder Text mit Effekten (fett, unterstrichen oder kursiv), haben Fenster Text Schriftart Farben oder abgeblendet, Schriftarten, Farben und können optional eine kleine Bitmap neben dem Dropdown-Element bereitstellen. Ähnlich wie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> Schnittstelle Bitmapbilder werden in Bildlisten bereitgestellt. Jede Dropdown-Kombination haben eine unterschiedliche Bildliste; Allerdings muss jeder Bildliste Abbilder mit gleicher Höhe enthalten. Außerdem ist die Verwendung der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> -Methode, Sie können eine QuickInfo für jede Kombination aus bereitstellen.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Rufen Sie diese Schnittstelle zum Erstellen oder zerstören der Dropdownleiste für ein Code-Fenster. Diese Schnittstelle kann auch verwendet werden, um festzustellen, ob eine Dropdownleiste bereits zu einem Codefenster, durch den Aufruf angefügt ist der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> Methode. Rufen Sie <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> für <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> aus <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Rufen Sie diese Schnittstelle direkt mit der Dropdownleiste kommunizieren. Sie können diese Schnittstelle verwenden, erzwingen der Aktualisierung von der Dropdown-Inhalt oder zum Ändern der Auswahl in einem der Listenfelder.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Wenn Sie registriert haben die `ShowDropdownBarOption` in Ihrer Sprache-Dienst-Registrierungsschlüssel, überwachen Sie dann Ihre Codefenster-Manager muss dieses Ereignis, um die Synchronisierung mit benutzereinstellungen bezüglich gibt an, ob die Dropdown-Leiste angezeigt werden soll. Wenn Sie diese Option nicht in der Sprache Dienstschlüssel registrieren, und klicken Sie dann die Option zum Anzeigen oder Ausblenden der Dropdownleiste ist deaktiviert, auf die **Optionen** Menü.  
  
## <a name="attach-a-drop-down-bar-to-a-code-window"></a>Fügen Sie eine Dropdownleiste an ein Code-Fenster  
 Zum Anfügen einer Dropdownleiste zum Code-Fenster bei der Erstellung ein Sprachdienst Anfügen muss, an der Dropdown-Statusleiste an, wenn die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> Methode wird aufgerufen. Wenn ein Aufruf von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> -Methode gibt an, dass eine Dropdownleiste noch nicht vorhanden sind und dann aufgerufen, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>. Für den Zugriff auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> Schnittstelle, rufen Sie <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> aus der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> Zeiger zurückgegeben, wenn Ihre <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> Implementierung wurde angefügt.  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen von Fenstern des Code mit der legacy-API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Unterstützung für die Navigationsleiste in einem legacy-Sprachdienst](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)