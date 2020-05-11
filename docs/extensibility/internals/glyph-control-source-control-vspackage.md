---
title: Glyphensteuerung (Quellcodeverwaltung VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9db1b4542eae293e39cda674fac3eb984aa77d3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708323"
---
# <a name="glyph-control-source-control-vspackage"></a>Glyphensteuerung (Quellcodeverwaltung VSPackage)
Ein Teil der tiefen Integration, die für die Quellcodeverwaltung VSPackages verfügbar ist, ist die Möglichkeit, ihre eigenen Glyphen anzuzeigen, um den Status von Elementen unter Quellcodeverwaltung anzuzeigen.

## <a name="levels-of-glyph-control"></a>Ebenen der Glyphensteuerung
 Eine Status-Glyphe ist ein Symbol, das den aktuellen Status eines Elements angibt, wenn es angezeigt wird, z. B. im **Projektmappen-Explorer** oder in der **Klassenansicht**. Ein Quellcodeverwaltungs-VSPackage kann zwei Ebenen der Glyphensteuerung ausüben. Es kann die Auswahl von Glyphen auf einen vordefinierten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Satz von Glyphen beschränken, die von der IDE bereitgestellt werden, oder es kann einen benutzerdefinierten Satz von Glyphen definieren, die angezeigt werden sollen.

### <a name="default-set-of-glyphs"></a>Standardsatz von Glyphen
 Um die Status-Glyphen zu ermitteln, die einem Element im **Projektmappen-Explorer**zugeordnet sind, fordert ein Projekt die Status-Glyphe aus der Quellcodeverwaltung mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>an. Ein Quellcodeverwaltungs-VSPackage kann entscheiden, die Auswahl von Glyphen auf vordefinierte Glyphen, die von der IDE bereitgestellt werden, beschränkt zu halten. In diesem Fall gibt das VSPackage ein Array von Werten zurück, die die Glyphenaufzählungen darstellen, die in *vsshell.idl*definiert sind. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Dies ist ein vordefinierter Satz von Glyphen, die von der IDE festgelegt werden, z. B. ein Vorhängeschloss für die eingecheckte Glyphe und ein Häkchen für die ausgecheckte Glyphe.

### <a name="custom-set-of-glyphs"></a>Benutzerdefinierter Satz von Glyphen
 Ein Quellcodeverwaltungs-VSPackage kann seine eigenen Glyphen für ein einzigartiges Aussehen und Gefühl verwenden, wenn es installiert ist. Wenn ein neues Quellcodeverwaltungs-VSPackage aktiv ist, sollte es in der Lage sein, seine eigenen Glyphen zu verwenden, auch wenn ein vorheriges Quellcodeverwaltungs-VSPackage noch geladen, aber inaktiv ist. In diesem Modus kann das Quellcodeverwaltungs-VSPackage weiterhin die vorhandenen Symbole [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwenden, um ein einheitliches Aussehen zu erhalten, wenn es dafür entscheidet.

 Der <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> Dienst unterstützt <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>eine Schnittstelle, die das VSPackage optional implementieren kann und die von der IDE angefordert wird. Wenn die IDE eine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Anforderung stellt, wird wiederum versuchen, diese Schnittstelle aus der aktuell registrierten Quellcodeverwaltung VSPackage abzubekommen. Wenn die Schnittstelle im registrierten VSPackage vorhanden ist, ist die Anforderung der IDE für benutzerdefinierte Glyphen erfolgreich. Andernfalls verwendet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die IDE den Standardsatz von Glyphen.

 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> Methode wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwendet, um eine Liste von Bildern zu erhalten, die verschiedene Quellcodeverwaltungszustände anzeigen. Das Quellcodeverwaltungs-VSPackage gibt der IDE ein Handle für seine benutzerdefinierten Glyphen in die Bildliste zurück. Die IDE erstellt an dieser Stelle eine Kopie der Bildliste und verwendet sie später, um die anzuzeigenden Glyphen auszuwählen. Wenn die neue Schnittstelle nicht `IVsSccGlyphs::GetCustomGlyphList` unterstützt `E_NOTIMPL`wird oder die Methode zurückkehrt, ruft die IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ihre Glyphen aus der Standardliste der von bereitgestellten Glyphen ab.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
