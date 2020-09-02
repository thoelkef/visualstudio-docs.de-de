---
title: 'Vorgehensweise: Aktualisieren vorhandener Vorlagen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b56cf11057957b0eb99fc065ed26af10d8adfbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670584"
---
# <a name="how-to-update-existing-templates"></a>Gewusst wie: Aktualisieren vorhandener Vorlagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nachdem Sie eine Vorlage erstellt und die Dateien in einer ZIP-Datei komprimiert haben, möchten Sie die Vorlage vielleicht ändern. Dazu können Sie die Dateien in der Vorlage manuell ändern oder aber eine neue Vorlage aus einem Projekt exportieren, das auf der Vorlage basiert.

## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>Verwenden des Assistenten "Vorlage exportieren" zum Aktualisieren einer vorhandenen Vorlage
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] stellt den Assistenten zum **Exportieren von Vorlagen** bereit, der zum Aktualisieren einer vorhandenen Vorlage verwendet werden kann.

#### <a name="to-use-export-template-to-update-an-existing-template"></a>So aktualisieren Sie eine vorhandene Vorlage mit "Vorlage exportieren"

1. Klicken Sie im Menü **Datei** auf **Neu** und dann auf **Neues Projekt**.

2. Wählen Sie die zu aktualisierende Vorlage aus, geben Sie einen Namen und Speicherort für das temporäre Projekt ein, und klicken Sie auf **OK**.

3. Ändern Sie das Projekt in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. Klicken Sie im Menü **Datei** auf **Vorlage exportieren**, und erstellen Sie im Assistenten zum **Exportieren von Vorlagen** eine neue Vorlage.

5. Nachdem die aktualisierte Vorlage in einer ZIP-Datei komprimiert wurde, löschen Sie die alte ZIP-Datei der Vorlage.

## <a name="manually-updating-an-existing-template"></a>Manuelles Aktualisieren vorhandener Vorlagen
 Sie können eine vorhandene Vorlage außerhalb von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aktualisieren, indem Sie die in der komprimierten ZIP-Datei enthaltenen Dateien ändern.

#### <a name="to-manually-update-an-existing-template"></a>So aktualisieren Sie eine vorhandene Vorlage manuell

1. Suchen Sie die ZIP-Datei, die die Vorlage enthält. Standardmäßig befindet sich diese Datei im Verzeichnis \Eigene Dateien\Visual Studio *Version*\My Exported Templates\\.

2. Extrahieren Sie die ZIP-Datei.

3. Ändern oder löschen Sie die aktuellen Vorlagendateien, oder fügen Sie der Vorlage neue Dateien hinzu.

4. Öffnen, ändern und speichern Sie die XML-Datei mit der Erweiterung .vstemplate, damit das geänderte Verhalten bzw. neue Dateien berücksichtigt werden. Weitere Informationen zum VSTEMPLATE-Schema finden Sie in der [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md). Weitere Informationen dazu, was Sie in den Quelldateien parametrisieren können, finden Sie unter [Vorlagen Parameter](../ide/template-parameters.md) .

5. Wählen Sie die Dateien in der Vorlage aus, klicken Sie mit der rechten Maustaste, klicken Sie auf **Senden an**, und klicken Sie dann auf **ZIP-komprimierter Ordner**. Die ausgewählten Dateien werden in einer ZIP-Datei komprimiert.

6. Fügen Sie die neue ZIP-Datei in demselben Verzeichnis ein, in dem sich auch die alte ZIP-Datei befand.

7. Löschen Sie die extrahierten Vorlagendateien und die alte ZIP-Datei der Vorlage.

8. Starten Sie (als Administrator) eine Instanz der Developer-Eingabeaufforderung (im Startmenü unter **Visual Studio 2010/Visual Studio-Tools/Developer-Eingabeaufforderung**).

9. Führen Sie den folgenden Befehl aus: `devenv /installvstemplates`.

## <a name="see-also"></a>Weitere Informationen
 [Anpassen von Vorlagen](../ide/customizing-project-and-item-templates.md) [Erstellen von Projekt-und Element Vorlagen](../ide/creating-project-and-item-templates.md) [Visual Studio-Vorlagen Schema Referenz](../extensibility/visual-studio-template-schema-reference.md) für Vorlagen [Parameter](../ide/template-parameters.md) Gewusst [wie: Erstellen von Starter Kits](../ide/how-to-create-starter-kits.md)
