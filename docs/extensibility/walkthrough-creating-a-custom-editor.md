---
title: 'Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7eb376637fd72f3856415ee2527ec622fea02950
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697668"
---
# <a name="walkthrough-create-a-custom-editor"></a>Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors
Die VSPackage-Projektvorlage kann einen einfachen benutzerdefinierten Editor in C++ erstellen. Die VSPackage-Projektvorlage unterstützt keine C- oder Visual Basic-Projekte mehr. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="prerequisites"></a>Voraussetzungen
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="the-visual-studio-package-project-template"></a>Die Visual Studio Package-Projektvorlage
 Die Visual Studio Package-Projektvorlage finden Sie im Dialogfeld **Neues Projekt** unter dem Ordner **C++-Erweiterbarkeit.**

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>So erstellen Sie ein VSPackage mit der Visual Studio-Paketvorlage

1. Erstellen Sie ein Projekt mit der Visual Studio-Paketvorlage.

2. Wählen Sie die Option **Benutzerdefinierter Editor** aus, und klicken Sie auf **Weiter**. Die Seite **Editoroptionen** wird angezeigt.

3. Geben Sie den Namen Ihres Editors in das Feld **Editorname** ein. Geben Sie die Dateierweiterung, die Dem Editor zugeordnet werden soll, in das Feld **Dateierweiterung** ein. Ihr Editor ist für Dateien mit dieser Erweiterung verfügbar. Die Dateierweiterung ist nur für Visual Studio registriert, nicht für Windows. Geben Sie den Standarddateinamen für neue Dokumente, die mit ihrem Editor erstellt wurden, in das Feld **Standarddateiname** ein.

4. Klicken Sie auf **Fertig stellen** , um Ihr VSPackage in dem von Ihnen angegebenen Ordner zu erstellen.

### <a name="to-test-your-custom-editor"></a>So testen Sie Ihren benutzerdefinierten Editor

1. Zeigen Sie im Menü **Datei** auf **Neu,** und klicken Sie dann auf **Datei**.

2. Wählen Sie im Bereich Installierte Vorlagen im Dialogfeld **Neue Datei** die Dateivorlage und dann den **registrierten** Dateityp aus.

3. Klicken Sie auf **Öffnen,** um das Dokument anzuzeigen und zu bearbeiten.

     Der Editor unterstützt Cut-and-Paste-, Find-and-Replace- und Open-and-Load-Vorgänge.

## <a name="see-also"></a>Weitere Informationen
- [VSPackages](../extensibility/internals/vspackages.md)
