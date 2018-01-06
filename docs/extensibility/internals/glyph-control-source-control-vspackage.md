---
title: Symbol-Steuerelement (Source Control VSPackage) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e41fc2a7d09f50d70caca939e3fdd691b1d05c9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="glyph-control-source-control-vspackage"></a>Symbol-Steuerelement (Source Control VSPackage)
VSPackages Datenquellen zur Tiefen Integration gehört die Möglichkeit, eigene Symbole, um anzugeben, den Status von Elementen in der quellcodeverwaltung anzuzeigen.  
  
## <a name="levels-of-glyph-control"></a>Ebenen der Symbol-Steuerelement  
 Ein Status-Symbol ist ein Symbol, das den aktuellen Status eines Elements, wenn angezeigt, z. B. in angibt **Projektmappen-Explorer** oder im **Klassenansicht**. Ein Datenquellen-Steuerelement VSPackage Formularvorlagen zwei Ebenen der Symbol-Steuerelement. Sie können die Auswahl von Symbolen, die einen vordefinierten Satz von Glyphen gebotenen beschränken die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, oder sie können einen benutzerdefinierten Satz von Symbolen angezeigt werden definieren.  
  
### <a name="default-set-of-glyphs"></a>Standardsatz von Symbolen  
 Der Status-Symbole zu ermitteln, die ein Element in zugeordnet sind **Projektmappen-Explorer**, ein Projekt fordert das Symbol Status aus der Datenquelle Steuerelement mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>. Ein Datenquellen-Steuerelement kann VSPackage entscheiden, zu die Auswahl von Symbolen, beschränkt auf vordefinierte Symbole, die von der IDE bereitgestellt. In diesem Fall übergibt das VSPackage wieder ein Array von Werten, die die Symbol-Enumerationen, die in vsshell.idl definiert sind darstellt. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> . Dies ist ein vordefinierter Satz von Symbolen, die von der IDE, z. B. Sperren ein Vorhängeschlosssymbol für das Symbol "Eingecheckt" und ein Häkchen als das Symbol "Ausgecheckt" festgelegt.  
  
### <a name="custom-set-of-glyphs"></a>Benutzerdefinierte Gruppe von Symbolen  
 Ein Datenquellen-Steuerelement VSPackage können eigene Symbole für eine eindeutige "Erscheinungsbild" bei der Installation. Wenn eine neue Datenquellen-Steuerelements VSPackage aktiv ist, sollte es sein, starten, verwenden die eigene Symbole, selbst wenn eine vorherige Quelle steuern VSPackage wird noch geladen, aber nicht aktiv. In diesem Modus kann das Quellsteuerelement VSPackage weiterhin können die vorhandenen Symbole um einen Blick zu gewährleisten, die konsistent mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , wenn es auswählt.  
  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> Service unterstützt eine Schnittstelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, die das VSPackage optional implementieren kann und die werden für die von der IDE aufgefordert werden. Wenn die IDE eine Anforderung, sendet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] versucht dann, diese Schnittstelle nicht entnommen werden die aktuell registrierte quellcodeverwaltung VSPackage. Wenn die Schnittstelle in der registrierten VSPackage vorhanden ist, ist der IDE-Anforderung für benutzerdefinierte Symbole erfolgreich; andernfalls die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE verwendet der Standardsatz von Symbolen.  
  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> Methode wird verwendet, indem Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] so erhalten eine Liste der Images, die mit verschiedenen Datenquellen-Steuerelements Datenbankstatus an. Die Datenquellen-Steuerelements VSPackage gibt ein Handle auf die Bildliste für ihre benutzerdefinierte Symbole für die IDE aus. Die IDE eine Kopie der Bildliste an diesem Punkt und später verwendet zum Auswählen der Symbole, angezeigt. Wenn die neue Benutzeroberfläche nicht unterstützt wird oder die `IVsSccGlyphs::GetCustomGlyphList` Methodenrückgabe E_NOTIMPL zurück, und klicken Sie dann die IDE die Symbole aus der Standardliste von Symbolen, die vom ruft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>