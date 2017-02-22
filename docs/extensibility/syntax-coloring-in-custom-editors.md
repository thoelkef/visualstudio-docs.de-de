---
title: "Syntaxfarben in benutzerdefinierten Editoren | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] benutzerdefinierte - Farben für Syntax"
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Syntaxfarben in benutzerdefinierten Editoren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Editoren der Visual Studio\-Umgebung SDK, einschließlich den Kern des Editors, verwenden Sprachendienste, um bestimmte syntaktische Elemente zu identifizieren und sie mit den angegebenen Farben für eine Ansicht eines bestimmten Dokuments angezeigt wird.  
  
## Farbauftrag\-Anforderungen  
 Alle Editoren, die eine farbige Darstellung des Sprachdiensts müssen implementiert werden:  
  
1.  Verwenden Sie ein Objekt, das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> implementiert, um den Text getönt werden soll, und ein Objekt zu verwalten, das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> implementiert, um eine Ansicht des Texts Dokumente bereitzustellen.  
  
2.  Rufen Sie eine Schnittstelle zu einem bestimmten Sprachdienst, indem sie den VSPackages Dienstanbieter abfragt, der das identifizierende GUID des Sprachdiensts verwendet.  
  
3.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>\-Methode des Objekts auf, das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>implementiert.  Diese Methode ordnet den Sprachdienst mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Implementierung zu VSPackages, der verwendet wird, um den Text zu verwalten, der getönt werden soll.  
  
## Kern\-Editor\-Verwendung einer farbigen Darstellung des Sprachdiensts  
 Wenn ein Sprachdienst mit einem farbigen Darstellung von einer Instanz des zentralen editors abgerufen wird, wird die Analyse und das Rendern von Text durch eine farbige Darstellung des Sprachdiensts automatisch auf, ohne weitere Komponenten auf dem Intervention erforderlich ist.  
  
 Die IDE transparent:  
  
-   Ruft die farbige Darstellung bei Bedarf auf, um Text zu analysieren und zu analysieren, wie sie in der Implementierung von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>hinzugefügt oder geändert wird.  
  
-   Stellt sicher, dass die Anzeige, die von der Ansicht Dokumente aus der bereitgestellten <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Implementierung unter Verwendung der angegebenen Informationen aktualisiert und neu gezeichnet wird, die von der farbige Darstellung zurückgegeben werden.  
  
## Nichtkern\- Editor\-Verwendung einer farbigen Darstellung des Sprachdiensts  
 Editor Nichtkern\- Instanzen können einen Syntax farbauftrag auch mithilfe des Sprachdiensts für sie müssen jedoch explizit abrufen und die farbige Darstellung des Diensts zu übernehmen und ihr Dokument neu zu zeichnen verweist.  
  
 So fügen Sie dazu erfordert einen Nichtkern\- Editor:  
  
1.  Ruft ein Objekt mit farbigen Darstellung des Sprachdiensts \(das `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>implementiert\).  VSPackage geschieht, indem die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>\-Methode für die Schnittstelle des Sprachdiensts aufruft.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>\-Methode auf, um anzufordern, dass ein bestimmter Textabschnitt darfarbig gestellt wird.  
  
     Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>\-Methode gibt ein Array von Werten, einen für jeden Buchstaben im Textabschnitt zurück, der getönt werden soll.  Er gibt außerdem den Textabschnitt als ein bestimmter Typ färbbares Element, z. B. einen Kommentar ein Schlüsselwort oder einen Datentyp.  
  
3.  Verwenden Sie die Farbauftrag Informationen, die von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> zurückgegeben werden, um seinen Text anzuzeigen und neu zu zeichnen.  
  
> [!NOTE]
>  Neben der Verwendung einer farbigen Darstellung des Sprachdiensts, kann ein VSPackage die Möglichkeit, allgemeine Visual Studio\-Umgebung SDK TEXT farbton Mechanismus verwenden.  Weitere Informationen zu diesem Verfahren finden Sie unter [Verwenden von Schriftarten und Farben](../extensibility/using-fonts-and-colors.md).  
  
## Siehe auch  
 [Syntaxfarben in eine Legacy\-Sprachdienst](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementieren von Farben für Syntax](../extensibility/internals/implementing-syntax-coloring.md)   
 [Gewusst wie: Verwenden von integrierten Färbbare Elemente](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Benutzerdefinierte Färbbare Elemente](../extensibility/internals/custom-colorable-items.md)