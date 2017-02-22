---
title: "Dropdown-Leiste | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK], Legacy - Dropdown-Menüleiste"
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Dropdown-Leiste
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Dropdownliste Leiste wird oben im Fenster Code bereitgestellt und zwei Dropdownlisten enthält.  
  
## Leiste\-Schnittstellen Dropdownelement  
 In [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]zum Beispiel enthält die Dropdownliste Leiste Listen für [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]\-Element\-und [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]\-Element\-Memberfunktionen, wie im folgenden Bild gezeigt.  
  
 ![Dropdownlisten](../extensibility/media/vsdropdown_bar.png "vsDropdown\_bar")  
Dropdownfeld Leiste  
  
 Beim Erstellen einer Dropdownliste Leiste implementiert, gibt es vier Schnittstellen der höchsten Wichtigkeit:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implementieren Sie diese Schnittstelle, um den Inhalt der Dropdownliste Leiste eingefügt werden soll.  Jede Dropdownliste Kombination kann den Nur\-Text oder fantastischen Text enthalten \(Fett oder Kursiv, Unterstrichen Fenstertext\), kann farbton Schriftart oder abgeblendeten Schriftart farbton verfügen und kann eine kleine Bitmap Dropdownpfeil neben dem Element optional bereitstellen.  Ähnlich wie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>\-Schnittstelle, Bitmapbilder werden in Bildlisten enthalten.  Jede Dropdownliste Kombination kann eine andere Bildliste haben. Allerdings muss jede Bildliste Bilder der gleichen Höhe enthalten.  Darüber hinaus mithilfe der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A>\-Methode können Sie eine QuickInfo für jede Kombination bieten.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Rufen Sie diese Schnittstelle entweder erstellt oder zerstört die Dropdownliste Leiste für ein Codefenster an.  Diese Schnittstelle kann auch verwendet werden, um zu bestimmen, ob eine Dropdownliste Anzeige bereits einem Codefenster angefügt wird, indem Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A>\-Methode aufgerufen wird.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> für <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> Aufruf von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Rufen Sie diese Schnittstelle, um direkt mit der Dropdownliste Anzeige zu kommunizieren.  Mit dieser Schnittstelle können Sie eine Aktualisierung der Dropdownliste Inhalt der Leiste zu erzwingen oder die Auswahl in einem der Listenfelder zu ändern.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Wenn Sie im `ShowDropdownBarOption` registrierungsschlüssel Sprachdienst registriert haben, muss der Code fenster\-manager dieses Ereignis überwachen, um Benutzereinstellungen zu synchronisieren, ob die Dropdownliste Leiste angezeigt werden soll.  Wenn Sie diese Option nicht in der Tastatureingabe Sprachdienst registrieren, wird die Option, die Dropdownliste Anzeige ein\- oder ausgeblendet werden kann **Optionen** im Menü deaktiviert.  
  
## Eine Dropdownliste Leiste an einen Code\-Fenster anfügen  
 Um eine Dropdownliste Leiste zum Anfügen Codefenster wenn sie erstellt wird, sollte ein Sprachdienst der Dropdownliste Leiste an wenn die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>\-Methode aufgerufen wird.  Wenn ein Aufruf der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A>\-Methode angibt, dass eine Dropdownliste Anzeige nicht bereits vorhanden ist, rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>an.  Um die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>\-Schnittstelle zuzugreifen <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> Aufruf zurückgegebenen vom <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> Zeiger auf die Implementierung <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> Ihnen zurück als angefügt wurde.  
  
## Siehe auch  
 [Anpassen von Code Windows mit der Legacy\-API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Unterstützung für die Navigationsleiste in einem Legacy\-Sprachdienst](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)