---
title: VSIX-Projektvorlage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74791a77ee1c720fb60876a1efa6bd58fa94f68b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697936"
---
# <a name="vsix-project-template"></a>VSIX-Projektvorlage

Sie können die VSIX-Projektvorlage verwenden, um eine oder mehrere Visual Studio-Erweiterungen in einem VSIX-Projekt zu umschließen und das Paket dann auf der [Visual Studio Marketplace-Website](https://marketplace.visualstudio.com/) zu veröffentlichen.

 Die VSIX-Bereitstellung unterstützt VSPackages, Assemblys, MEF-Komponenten, Projektvorlagen, Elementvorlagen, Toolboxsteuerelemente und benutzerdefinierte Erweiterungstypen.

> [!NOTE]
> Um VSIX-Projekte verwenden zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen zum Visual Studio SDK finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="where-to-find-the-vsix-project-template"></a>Wo finden Sie die VSIX-Projektvorlage

Die VSIX-Projektvorlage ist im Dialogfeld **Neues Projekt** verfügbar, indem Sie nach "vsix" suchen.  Es gibt sowohl eine Version von C- als auch eine Visual Basic-Version.

> [!TIP]
> Stellen Sie sicher, dass .NET Framework 4.5 oder höher im Dropdown-Listenfeld oben im Dialogfeld **Neues Projekt** angegeben ist.

## <a name="uses-of-the-vsix-project-template"></a>Verwendung der VSIX-Projektvorlage

Die VSIX-Projektvorlage hat zwei Hauptverwendungen:

- So stellen Sie Projektvorlagen, Elementvorlagen und Erweiterungen bereit.

- Um die Ausgaben mehrerer Erweiterungen in einem Bereitstellungspaket zu umschließen.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Verpacken einer Erweiterung in einem leeren VSIX-Projekt

Sie können eine vorhandene Erweiterung oder eine Erweiterung, die noch keine VSIX-Unterstützung hat, verpacken, indem Sie sie in ein leeres VSIX-Projekt packen. Die zu umwickelnde Erweiterung muss von einem Typ sein, der vom [VSIX-Schema](../extensibility/vsix-extension-schema-2-0-reference.md)unterstützt wird.

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>So verpacken Sie eine Erweiterung mithilfe eines VSIX-Projekts

1. Erstellen Sie die Projekte, aus denen ihre Erweiterung erstellt wird.

2. Erstellen Sie ein VSIX-Projekt mithilfe der **VSIX-Projektvorlage.**

    *Source.extension.vsixmanifest* wird im **Manifest-Designer**geöffnet.

3. Wählen Sie auf der Registerkarte **Assets** die Schaltfläche **Neu** aus.

    Das Dialogfeld **Neues Objekt hinzufügen** wird angezeigt.

4. Wählen Sie in der **Liste Typ** den Erweiterungstyp aus, der hinzugefügt werden soll.

5. Führen Sie die folgenden Schritte aus, um eine Erweiterung oder ein Inhaltselement hinzuzufügen, das in der aktuellen Projektmappe enthalten ist (z. B. eine Elementvorlage oder eine kompilierte Assembly):

   1. Wählen Sie in der **Liste Quelle** die Option Ein Projekt in der **aktuellen Projektmappe**aus.

   2. Wählen Sie in der **Projektliste** den Namen der Erweiterung aus.

   3. Geben Sie im Feld **Einbettung in diesem Ordner** den Namen eines Ordners ein, in den das Asset eingebettet werden soll, und wählen Sie dann die Schaltfläche **OK** aus.

6. Führen Sie die folgenden Schritte aus, um eine Erweiterung oder ein Inhaltselement hinzuzufügen, das nicht in der aktuellen Lösung enthalten ist:

   1. Wählen Sie im Listenfeld **Quelle** **Datei im Dateisystem**aus.

   2. Geben Sie im Feld **Pfad** den vollständigen Pfad zur kompilierten oder komprimierten Erweiterungsdatei ein, oder verwenden Sie die Schaltfläche **Durchsuchen,** um zur Datei zu navigieren.

   3. Geben Sie im Feld **Einbettung in diesem Ordner** den Namen eines Ordners ein, in den das Asset eingebettet werden soll, und wählen Sie dann die Schaltfläche **OK** aus.

7. Wenn Ihr Paket zusätzliche Erweiterungen enthalten soll, fügen Sie sie auf die gleiche Weise hinzu.

8. Erstellen Sie die Projektmappe.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]erstellt eine *.vsix-Datei,* die eine VSIX-Manifestdatei, eine [Content_Types]*XML-Datei* und alle Erweiterungselemente enthält, die Sie dem Projekt hinzugefügt haben.

## <a name="see-also"></a>Weitere Informationen

- [VSIX-Erweiterungsschema 2.0-Referenz](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)
