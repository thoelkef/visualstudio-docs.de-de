---
title: Glyphensteuerung (Quellcodeverwaltungs-VSPackage) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f66613c5f5b8b6e48efda17330f66cdb87a06cf9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909906"
---
# <a name="glyph-control-source-control-vspackage"></a>Glyphensteuerung (Datenquellen-Steuerelement-VSPackage)
Die enge Integration zur quellcodeverwaltung VSPackages gehört die Möglichkeit, eigene Symbole, um anzugeben, den Status von Elementen unter quellcodeverwaltung anzuzeigen.

## <a name="levels-of-glyph-control"></a>Ebenen der Symbol-Steuerelement
 Ein Symbol Status ist ein Symbol, das den aktuellen Status eines Elements, bei der Anzeige, z. B. in angibt **Projektmappen-Explorer** oder im **Klassenansicht**. Ein Quellcodeverwaltungs-VSPackage kann auf zwei Ebenen der glyphensteuerung ausführen. Sie können die Auswahl von Symbolen, die einen vordefinierten Satz von Symbolen, die von bereitgestellte beschränken die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, oder sie können definieren, einen benutzerdefinierten Satz von Symbolen, die angezeigt werden soll.

### <a name="default-set-of-glyphs"></a>Der Standardsatz von Symbolen
 Die Symbole Status zu ermitteln, die ein Element in zugeordnet sind **Projektmappen-Explorer**, ein Projekt wird die inhaltsortsanfrage des Symbols Zustand Datenquellen-Steuerelement mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>. Ein Datenquellen-Steuerelement können VSPackage, zu die Auswahl von Symbolen, beschränkt auf vordefinierte Symbole, die von der IDE bereitgestellt. In diesem Fall das VSPackage übergibt ein Array von Werten, die die Symbol-Enumerationen, die in definierten darstellt *vsshell.idl*. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Dies ist ein vordefinierter Satz von Symbolen, die festlegen, die von der IDE, z. B. ein Vorhängeschlosssymbol für das Symbol eingecheckt und mit einem Häkchen versehen für das Symbol ausgecheckt.

### <a name="custom-set-of-glyphs"></a>Benutzerdefinierte Gruppe von Symbolen
 Ein Quellcodeverwaltungs-VSPackage können eigene Symbole für eine eindeutige Aussehen und Verhalten bei der Installation. Wenn ein neues Quellcodeverwaltungs-VSPackage aktiv ist, sollte es sein, können Sie beim Einstieg in eine eigene Symbole, auch wenn eine vorherige Quelle VSPackage zu steuern, wird immer noch geladen, aber nicht aktiv. In diesem Modus kann das Quellcodeverwaltungs-VSPackage trotzdem können die vorhandenen Symbole um einiges zu gewährleisten, die konsistent mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , wenn es auswählt.

 Die <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> -Dienst unterstützt eine Schnittstelle, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, die das VSPackage implementieren kann, und die werden für die von der IDE aufgefordert werden. Wenn die IDE eine Anforderung, stellt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wiederum versucht, diese Schnittstelle aus der die aktuell registrierte quellcodeverwaltung VSPackage abrufen. Wenn die Schnittstelle im registrierten VSPackage vorhanden ist, erfolgreich ausgeführt wird die IDE Anforderung für benutzerdefinierte Symbole andernfalls die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE verwendet einen standardmäßigen Satz von Symbolen.

 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> Methode wird verwendet, indem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zum Abrufen einer Liste der Images, die mit verschiedenen Datenquellen-Steuerelement angibt. Das Quellcodeverwaltungs-VSPackage gibt ein Handle für die Bildliste für die benutzerdefinierte Symbole für die IDE aus. Die IDE eine Kopie der Bildliste an diesem Punkt und verwendet es später noch Mal auf die Symbole angezeigt. Wenn die neue Schnittstelle nicht unterstützt wird oder die `IVsSccGlyphs::GetCustomGlyphList` Methodenrückgabe `E_NOTIMPL`, und klicken Sie dann die IDE die Glyphen aus der Standardliste von Symbolen, die vom ruft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>