---
title: 'Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eca6bc68accfd5c33e439ddfc5709943be7b549e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312761"
---
# <a name="walkthrough-create-a-custom-editor"></a>Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors
Die VSPackage-Projektvorlage kann einen einfachen, benutzerdefinierten Editor in C++ erstellen. Die VSPackage-Projektvorlage wird C#- oder Visual Basic-Projekte nicht mehr unterstützt. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="prerequisites"></a>Vorraussetzungen
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="the-visual-studio-package-project-template"></a>Die Visual Studio-Paket-Projektvorlage
 Sie finden die Visual Studio-Paket-Projektvorlage in das **neues Projekt** Dialogfeld unter die **C++-Erweiterungen** Ordner.

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>So erstellen Sie eine VSPackage mithilfe der Visual Studio-Paketvorlage

1. Erstellen Sie ein Projekt mit der Visual Studio-Paket-Vorlage.

2. Wählen Sie die **Editor für benutzerdefinierte** aus, und klicken Sie auf **Weiter**. Die **Editoroptionen** Seite wird angezeigt.

3. Geben Sie den Namen des Editors in die **editorname** Feld. Geben Sie die Dateierweiterung, die Ihr Editor im zugeordnet werden sollen die **Dateierweiterung** Feld. Ihre-Editor ist für Dateien mit dieser Erweiterung verfügbar. Die Dateierweiterung ist nicht für Windows nur für Visual Studio registriert. Geben Sie der Standarddateiname für neue Dokumente erstellt, die mit Ihrem-Editor in die **Standarddateiname** Feld.

4. Klicken Sie auf **Fertig stellen** , um Ihr VSPackage in dem von Ihnen angegebenen Ordner zu erstellen.

### <a name="to-test-your-custom-editor"></a>Zum Testen des benutzerdefinierten Editors

1. Auf der **Datei** Startmenü **neu** , und klicken Sie dann auf **Datei**.

2. In der **installierte Vorlagen** im Bereich der **neue Datei** wählen Sie im Dialogfeld die Dateivorlage, und klicken Sie dann auf die Datei, Sie registriert geben.

3. Klicken Sie auf **öffnen** anzeigen und bearbeiten das Dokument.

     Der Editor unterstützt Ausschneiden und einfügen, suchen und ersetzen und Open-and-Load-Vorgänge.

## <a name="see-also"></a>Siehe auch
- [VSPackages](../extensibility/internals/vspackages.md)