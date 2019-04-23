---
title: 'Vorgehensweise: Verwenden Sie eine Ressourcendatei zum Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2be88a29d3e9e3da9d1963aa1226ffca0a0a2bbd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066532"
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>Vorgehensweise: Verwenden Sie eine Ressourcendatei zum Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen
  Verwenden Sie eine Ressourcendatei, können Sie lokalisierte Namen, Eigenschaften zu definieren und Anwenden von Berechtigungen Tor-Objekte, die in einem Business Data Connectivity (BDC)-Modell definiert sind. Um diese Informationen anzugeben, fügen Sie eine **Business Data Connectivity-Ressource** Element, das ein Projekt mit einem **Business Data Connectivity-Modells** Element. Dann geben Sie Namen, Eigenschaften und Berechtigungen durch Bearbeiten den XML-Code für die Ressourcendatei.

### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Eine BDC-Ressourcendatei einem SharePoint-Projekt hinzu

1. In **Projektmappen-Explorer**, erweitern Sie den Ordner für die SharePoint-Projekt, und wählen Sie dann den Ordner mit dem BDC-Modell.

2. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

3. Erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.

4. In der **neues Element hinzufügen** Dialogfeld wählen **Business Data Connectivity-Ressourcenelement**.

5. In der **Namen** Feld Geben Sie den Namen der Ressourcendatei, und wählen Sie dann die **hinzufügen** Schaltfläche.

     Eine Ressourcendatei, die der Erweiterung .bdcr wird dem Projekt hinzugefügt und für die Bearbeitung geöffnet.

6. Fügen Sie XML-Code, um definieren den lokalisierten Namen, Eigenschaften und Berechtigungen, die auf das BDC-Modell angewendet werden soll.

     Weitere Informationen zum Definieren dieser Elemente finden Sie unter [Modell und Ressourcendateien](http://go.microsoft.com/fwlink/?LinkID=169283).

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Vorgehensweise: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)
- [Vorgehensweise: Einfügen einer benutzerdefinierten Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
