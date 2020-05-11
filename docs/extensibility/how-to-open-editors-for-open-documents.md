---
title: 'Gewusst wie: Öffnen von Editoren für offene Dokumente | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d0986573ac0d53427f6490370be2bfa1c4cbe7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710913"
---
# <a name="how-to-open-editors-for-open-documents"></a>Gewusst wie: Öffnen von Editoren für geöffnete Dokumente
Bevor ein Projekt ein Dokumentfenster öffnet, muss das Projekt zunächst bestimmen, ob die Datei bereits im Dokumentfenster für einen anderen Editor geöffnet ist. Die Datei kann entweder in einem projektspezifischen Editor oder in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]einem der Standard-Editoren geöffnet sein, die bei registriert sind.

## <a name="open-a-project-specific-editor"></a>Öffnen eines projektspezifischen Editors
 Verwenden Sie das folgende Verfahren, um einen projektspezifischen Editor für eine datei zu öffnen, die bereits geöffnet ist.

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>So öffnen Sie einen projektspezifischen Editor für eine geöffnete Datei

1. Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> -Methode auf.

    Dieser Aufruf gibt Zeiger auf die Hierarchie, das Hierarchieelement und den Fensterrahmen des Dokuments zurück.

2. Wenn das Dokument geöffnet ist, muss das Projekt überprüfen, ob nur ein Dokumentdatenobjekt vorhanden ist oder ob auch ein Dokumentansichtsobjekt vorhanden ist.

   - Wenn ein Dokumentansichtsobjekt vorhanden ist und diese Ansicht für ein anderes Hierarchie- oder Hierarchieelement gilt, verwendet das Projekt den Zeiger auf den Fensterrahmen der Ansicht, um das vorhandene Fenster wieder aufzutauchen.

   - Wenn ein Dokumentansichtsobjekt vorhanden ist und diese Ansicht für dasselbe Hierarchie- und Hierarchieelement gilt, kann das Projekt eine zweite Ansicht öffnen, wenn es an das zugrunde liegende Dokumentdatenobjekt angefügt werden kann. Andernfalls sollte das Projekt den Zeiger auf den Fensterrahmen der Ansicht verwenden, um das vorhandene Fenster wieder aufzutauchen.

   - Wenn nur das Dokumentdatenobjekt vorhanden ist, sollte das Projekt bestimmen, ob es das Dokumentdatenobjekt für seine Ansicht verwenden kann. Wenn das Dokumentdatenobjekt kompatibel ist, führen Sie die unter [Öffnen eines projektspezifischen Editors](../extensibility/how-to-open-project-specific-editors.md)beschriebenen Schritte aus.

     Wenn das Dokumentdatenobjekt nicht kompatibel ist, sollte dem Benutzer ein Fehler angezeigt werden, der angibt, dass die Datei gerade verwendet wird. Dieser Fehler sollte nur in vorübergehenden Fällen angezeigt werden, z. B. wenn eine Datei gleichzeitig kompiliert wird, versucht der Benutzer, die Datei mit einem anderen Editor als dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Kerntexteditor zu öffnen. Der Kerntexteditor kann Dokumentdatenobjekte für den Compiler freigeben.

3. Wenn das Dokument nicht geöffnet ist, da kein Dokumentdatenobjekt oder Dokumentansichtsobjekt vorhanden ist, führen Sie die Schritte unter [Öffnen eines projektspezifischen Editors](../extensibility/how-to-open-project-specific-editors.md)aus.

## <a name="open-a-standard-editor"></a>Öffnen eines Standard-Editors
 Verwenden Sie das folgende Verfahren, um einen Standard-Editor für eine datei zu öffnen, die bereits geöffnet ist.

### <a name="to-open-a-standard-editor-for-an-open-file"></a>So öffnen Sie einen Standard-Editor für eine geöffnete Datei

1. Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> auf.

     Diese Methode überprüft zunächst, ob das Dokument <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>nicht bereits geöffnet ist, indem sie aufruft. Wenn das Dokument bereits geöffnet ist, wird das Editorfenster wieder geöffnet.

2. Wenn das Dokument nicht geöffnet ist, führen Sie die Schritte unter [Gewusst wie: Öffnen von Standardeditoren](../extensibility/how-to-open-standard-editors.md)aus.

## <a name="see-also"></a>Weitere Informationen
- [Öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md)
- [Gewusst wie: Öffnen sie projektspezifische Editoren](../extensibility/how-to-open-project-specific-editors.md)
- [Gewusst wie: Öffnen von Standard-Editoren](../extensibility/how-to-open-standard-editors.md)
