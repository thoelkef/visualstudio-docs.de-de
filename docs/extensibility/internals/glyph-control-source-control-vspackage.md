---
title: "Symbol-Steuerelement (Source Control VSPackage) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Symbole, Source Control-Pakete"
  - "Quellcode-Verwaltungspaketen, Symbole"
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Symbol-Steuerelement (Source Control VSPackage)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Der Teil der tiefen die Integration der Quellcodeverwaltung VSPackages verfügbar ist, ist die Möglichkeit, eigene Symbole anzeigen, um den Status von Elementen in einem Quellcodeverwaltungssystem anzugeben.  
  
## Ebenen des Symbol\-Steuerelements  
 Ein Symbol Zustand ist ein Symbol, das den aktuellen Status eines Elements angibt, wenn es zum Beispiel in **Projektmappen\-Explorer** oder **Klassenansicht**angezeigt wird.  Eine Quellcodeverwaltung VSPackage kann zwei Ebenen Symbol für abdecken.  Es kann die Auswahl von Symbolen in einen vordefinierten Satz von Symbolen, die vom [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE bereitgestellt werden, oder es kann ein benutzerdefiniertes definieren, die von den anzuzeigenden Symbols festgelegt ist.  
  
### Standard\-Satz Symbole  
 Um die Symbole Zustände, die einem Element zugeordnet sind, in **Projektmappen\-Explorer**Anforderungen Symbol Zustände eines Projekts aus der Quellcodeverwaltung mit dem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>bestimmen.  Eine Quellcodeverwaltung VSPackage entscheidet, um die Auswahl von Symbolen zu speichern, die an den vordefinierten Symbole beschränkt werden, die in der IDE bereitgestellt werden.  In diesem Fall wird wieder VSPackages ein Array von Werten, das Symbol enumerationen darstellt, die in vsshell.idl definiert sind.  Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> . Dies ist ein vordefinierter Satz von Symbolen, die von der IDE, z. B. ein Vorhängeschloß für das „Symbol“ aktiviert sind festgelegt werden, und ein Häkchen, z. B. „out“ Symbol überprüfen.  
  
### Benutzerdefiniertes Gruppe von Symbolen  
 Eine Quellcodeverwaltung VSPackage können eigene Symbole für ein eindeutiges „Erscheinungsbild“ verwenden, wenn sie installiert ist.  Wenn eine neue Quellcodeverwaltung VSPackage aktiv ist, sollte es möglich sein, mit seiner eigenen Symbole zu starten, selbst wenn eine vorherige Quellcodeverwaltung VSPackages deaktiviert jedoch weiterhin geladen wird.  In diesem Modus kann die Quellcodeverwaltung ein VSPackage die vorhandenen Symbole verwenden weiterhin beizubehalten Suchen, um ein, das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] konsistent sind, wenn sie ausgewählt werden.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> unterstützt eine Schnittstelle, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, die VSPackages und optional implementieren kann, um die IDE aufgefordert wird.  Wenn die IDE einen Anforderung [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wiederum versucht, diese Schnittstelle aus der aktuell registrierten Quellcodeverwaltung VSPackage abzurufen.  Wenn die Schnittstelle in registrierten VSPackage ist, wird die Anforderung der IDE um benutzerdefinierte Symbole. Andernfalls wird das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE den Standardsatz von Symbolen.  
  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A>\-Methode wird von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zum Abrufen einer Liste von Bildern, die unterschiedliche Zustände Quellcodeverwaltung anzeigen.  Die Quellcodeverwaltung VSPackage wird in der IDE ein Handle für die Bildliste für seine benutzerdefinierten Symbolen zurück.  Die IDE erstellt eine Kopie der Bildliste an dieser Stelle und verwendet sie später, um die Symbole auszuwählen, die angezeigt werden sollen.  Wenn die neue Schnittstelle nicht unterstützt wird oder die `IVsSccGlyphs::GetCustomGlyphList`\-Methode E\_NOTIMPL zurückgibt, ruft die IDE die zugehörigen Symbole der Standardliste von Symbolen ab, die von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]angegeben werden.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>