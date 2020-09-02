---
title: Glyphe-Steuerelement (Quellcodeverwaltungs-VSPackage) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b0960209b67c8d2f111296840119807d95bb2e2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538420"
---
# <a name="glyph-control-source-control-vspackage"></a>Glyphensteuerung (Quellcodeverwaltungs-VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Teil der umfassenden Integration, der für Quell Code Verwaltungs-VSPackages verfügbar ist, ist die Möglichkeit, eigene Symbole anzuzeigen, um den Status von Elementen unter Quell Code Verwaltung anzuzeigen.  
  
## <a name="levels-of-glyph-control"></a>Ebenen des Glyphe-Steuer Elements  
 Ein Statussymbol ist ein Symbol, das den aktuellen Status eines Elements anzeigt, wenn es angezeigt wird, z. b. in **Projektmappen-Explorer** oder **Klassenansicht**. Ein Quellcodeverwaltungs-VSPackage kann zwei Ebenen des Glyphe-Steuer Elements ausführen. Sie kann die Wahl der Symbole auf einen vordefinierten Satz von Symbolen beschränken, die von der IDE bereitgestellt werden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , oder es kann eine benutzerdefinierte Gruppe von Symbolen definiert werden, die angezeigt werden soll.  
  
### <a name="default-set-of-glyphs"></a>Standardsatz von Symbolen  
 Um die Statussymbole zu ermitteln, die einem Element in **Projektmappen-Explorer**zugeordnet sind, fordert ein Projekt das Zustands Symbol aus der Quell Code Verwaltung mithilfe von an <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A> . Ein Quellcodeverwaltungs-VSPackage kann entscheiden, dass die Auswahl der Glyphen auf vordefinierte Glyphen beschränkt ist, die von der IDE bereitgestellt werden. In diesem Fall gibt das VSPackage ein Array von Werten zurück, die die in vsshell. idl definierten Glyphe-Enumerationen darstellen. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> . Dies ist ein vordefinierter Satz von Symbolen, die von der IDE festgelegt werden, z. b. ein Vorhängeschloss für das Symbol "eingecheckt" und ein Häkchen als Symbol "ausgecheckt".  
  
### <a name="custom-set-of-glyphs"></a>Benutzerdefinierter Satz von Symbolen  
 Ein Quellcodeverwaltungs-VSPackage kann seine eigenen Symbole für ein eindeutiges "Aussehen und fühlen" verwenden, wenn es installiert wird. Wenn ein neues VSPackage für die Quell Code Verwaltung aktiv ist, sollte es in der Lage sein, eigene Symbole zu verwenden, auch wenn ein vorheriges VSPackage für die Quell Code Verwaltung noch geladen, aber inaktiv ist. In diesem Modus kann das VSPackage für die Quell Code Verwaltung die vorhandenen Symbole weiterhin verwenden, um ein Aussehen in Übereinstimmung mit zu behalten [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Der <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> Dienst unterstützt eine Schnittstelle, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> , die das VSPackage optional implementieren kann und die von der IDE angefordert werden. Wenn die IDE eine Anforderung sendet, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] versucht wiederum, diese Schnittstelle aus dem aktuell registrierten VSPackage für die Quell Code Verwaltung zu erhalten. Wenn die Schnittstelle im registrierten VSPackage vorhanden ist, ist die Anforderung der IDE für benutzerdefinierte Symbole erfolgreich. Andernfalls verwendet die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE ihren Standardsatz von Symbolen.  
  
 Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> Methode wird von verwendet [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , um eine Liste von Bildern zu erhalten, die verschiedene Quell Code Verwaltungs Zustände anzeigen. Das VSPackage der Quell Code Verwaltung kehrt der IDE ein Handle für die Bildliste für seine benutzerdefinierten Symbole hinzu. Die IDE erstellt an dieser Stelle eine Kopie der Bildliste und verwendet Sie später, um die anzuzeigenden Symbole auszuwählen. Wenn die neue Schnittstelle nicht unterstützt wird oder die `IVsSccGlyphs::GetCustomGlyphList` Methode E_NOTIMPL zurückgibt, ruft die IDE die Symbole aus der Standardliste von Symbolen ab, die von bereitgestellt werden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
