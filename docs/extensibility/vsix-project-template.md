---
title: VSIX-Projektvorlage | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92db48197791bab4b5f364ee6d2cd0e948e2a5f7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56684584"
---
# <a name="vsix-project-template"></a>VSIX-Projektvorlage
Sie können die VSIX-Projektvorlage verwenden, um eine oder mehrere Visual Studio-Erweiterungen in einer VSIX-Projekt zu umschließen und veröffentlichen Sie das Paket klicken Sie dann auf die [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) Website.

 VSIX-Bereitstellung unterstützt VSPackages, Assemblys, MEF-Komponenten, Projektvorlagen, Elementvorlagen, Toolbox-Steuerelemente und benutzerdefinierte Erweiterungstypen.

> [!NOTE]
>  Um die VSIX-Projekte verwenden zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen zu Visual Studio SDK, finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="where-to-find-the-vsix-project-template"></a>Wo finden die VSIX-Projektvorlage
 Die VSIX-Projektvorlage finden Sie in der **neues Projekt** Dialogfeld. Erweitern Sie entweder die **Visual Basic** Knoten oder die **Visual C#-** Knoten, und wählen Sie dann **Erweiterbarkeit**.

> [!TIP]
>  Sie sollten sicherstellen, dass diese .NET Framework 4.5 oder höher angegeben ist, klicken Sie im Dropdown-Liste am oberen Rand der **neues Projekt** Dialogfeld.

## <a name="uses-of-the-vsix-project-template"></a>Verwendet die VSIX-Projektvorlage
 Die VSIX-Projektvorlage verfügt über zwei Hauptanwendungsgebiete:

- Zum Bereitstellen von Projektvorlagen, Elementvorlagen und anderen Erweiterungen, die VSIX-Unterstützung nicht noch.

- Um die Ausgaben an mehreren Erweiterungen in ein Bereitstellungspaket zu umschließen.

  Sie müssen nicht die VSIX-Projektvorlage verwenden, für die Bereitstellung VSPackages oder andere Arten von Erweiterungen, die bereits VSIX unterstützen.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Verpacken einer Erweiterung in ein leeres VSIX-Projekt
 Sie können Packen einer vorhandenen Erweiterung oder eine Erweiterung, die noch kein VSIX-Unterstützung durch Einbinden in ein leeres VSIX-Projekt vorhanden ist. Die Erweiterung, die eingeschlossen werden muss von einem Typ sein, die von unterstützt wird die [VSIX-Schema](../extensibility/vsix-extension-schema-2-0-reference.md).

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Um eine Erweiterung mithilfe eines VSIX-Projekts zu verpacken.

1. Erstellen Sie die Projekte, aus denen die Erweiterung besteht.

2. Erstellen Sie ein VSIX-Projekt mithilfe der **VSIX-Projekt** Vorlage.

    *"Source.Extension.vsixmanifest"* öffnet im **Manifest-Designer**.

3. Auf der **Assets** Registerkarte die **neu** Schaltfläche.

    Die **neue Anlage hinzufügen** Dialogfeld wird angezeigt.

4. In der **Typ** Liste, wählen Sie den Typ der hinzuzufügenden Erweiterung.

5. Um ein Element-Erweiterung oder Inhalt hinzuzufügen, die in der aktuellen Projektmappe (z. B. eine Item-Vorlage oder eine kompilierte Assembly) enthalten ist, führen Sie die folgenden Schritte aus:

   1.  In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.

   2.  In der **Projekt** Liste, wählen Sie den Namen der Erweiterung.

   3.  In der **Einbetten in diesem Ordner** Geben Sie den Namen eines Ordners, in dem das Asset einbetten, und wählen Sie dann die **OK** Schaltfläche.

6. Zum Hinzufügen einer Erweiterung oder Content-Element, das nicht in der aktuellen Projektmappe enthalten ist, führen Sie die folgenden Schritte aus:

   1.  In der **Quelle** , und wählen Sie im Listenfeld **Datei im Dateisystem**.

   2.  In der **Pfad** Feld, geben Sie den vollständigen Pfad der kompilierten oder komprimierten Erweiterungsdatei oder verwenden Sie die **Durchsuchen** Schaltfläche, um die Datei zu suchen.

   3.  In der **Einbetten in diesem Ordner** Geben Sie den Namen eines Ordners, in dem das Asset einbetten, und wählen Sie dann die **OK** Schaltfläche.

7. Wenn Sie Ihr Paket zusätzliche Erweiterungen gehören möchten, fügen sie auf die gleiche Weise hinzu.

8. Erstellen Sie die Projektmappe.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt eine *VSIX* Datei, die eine VSIX-Manifestdatei, eine [Content_Types] enthält*XML* Datei und alle Ressourcen Erweiterung, die Sie dem Projekt hinzugefügt.

## <a name="see-also"></a>Siehe auch
- [Referenz zum VSIX-Erweiterung Schema 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)