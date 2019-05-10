---
title: 'Vorgehensweise: Hinzufügen und Entfernen von Funktionsabhängigkeiten | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9373ed07ec49bd41dad343dc447b4b2026793492
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967004"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Vorgehensweise: Hinzufügen und Entfernen von funktionsabhängigkeiten
  Die SharePoint-Funktion kann von anderen Funktionen für Funktionen oder Daten abhängen. In diesen Fällen können Sie diese anderen Funktionen als Abhängigkeiten für das Feature markieren. Auf diese Weise wird der SharePoint-Server sichergestellt, abhängigen Features aktiviert werden, bevor das Feature aktiviert ist.

## <a name="add-dependencies"></a>Hinzufügen von Abhängigkeiten
 Sie können andere Funktionen in der Projektmappe als Abhängigkeiten hinzufügen. Auf diese Weise können Sie sicherstellen, dass es sich bei benötigten Funktionen installiert und aktiviert werden, bevor die Funktion installiert ist.

#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Hinzufügen eine Abhängigkeit auf einer Funktion in der Projektmappe

1. Die Funktions-Designer öffnen, erweitern Sie die **Funktionsaktivierungsabhängigkeiten** Knoten, und wählen Sie dann die **hinzufügen** Schaltfläche.

2. In der **Funktionsaktivierungsabhängigkeiten hinzufügen** Dialogfeld auf die **Funktionen in der Projektmappe eine Abhängigkeit hinzufügen** Optionsfeld, wählen Sie den Titel der Funktion, die Sie als eine Abhängigkeit hinzufügen möchten und klicken Sie dann Wählen Sie die **hinzufügen** Schaltfläche.

     Sie können mehrere Funktionen hinzufügen, indem Sie mehrere Titel auswählen, bei der Auswahl der **STRG** Schlüssel.

## <a name="addi-custom-dependencies"></a>Benutzerdefinierter Addi-Abhängigkeiten
 Sie können Funktionen, die bereits bereitgestellt wurden, auf einem SharePoint-Server als Abhängigkeit hinzufügen. Auf diese Weise überprüft der SharePoint-Aktivierung, um sicherzustellen, dass alle abhängigen Features aktiviert werden, bevor die Funktion installiert ist.

#### <a name="to-add-a-dependency-by-the-feature-id"></a>Hinzufügen eine Abhängigkeit von der Feature-ID

1. Die Funktions-Designer öffnen, erweitern Sie die **Funktionsaktivierungsabhängigkeiten** Knoten, und wählen Sie dann die **hinzufügen** Schaltfläche.

2. In der **Funktionsaktivierungsabhängigkeiten hinzufügen** Dialogfeld auf die **benutzerdefinierte Abhängigkeit hinzufügen** Optionsfeld aus.

3. In der **Funktions-ID** Text Geben Sie die GUID für die Funktion, die Sie verwenden möchten, markieren Sie als eine aktivierungsabhängigkeit, und wählen Sie dann die **hinzufügen** Schaltfläche.

## <a name="edit-custom-dependencies"></a>Bearbeiten benutzerdefinierte Abhängigkeiten
 Sie können benutzerdefinierte Abhängigkeiten bearbeiten, die Sie zuvor hinzugefügt haben. Abhängige Funktionen, die in der Projektmappe können nur entfernt werden, jedoch nicht mehr bearbeitet.

#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>So ändern Sie eine Abhängigkeit für eine Funktion in der Projektmappe

1. Öffnen Sie die Funktions-Designer, und erweitern Sie dann die **Funktionsaktivierungsabhängigkeiten** Knoten.

2. Wählen Sie den Namen der Funktion, die Sie bearbeiten möchten, und wählen Sie dann die **bearbeiten** Schaltfläche.

3. In der **benutzerdefinierte Funktionsaktivierungsabhängigkeit bearbeiten** im Dialogfeld ändern Sie den Titel, Funktions-ID oder Beschreibung, und wählen Sie dann die **senden** Schaltfläche.

## <a name="remove-dependencies"></a>Entfernen Sie Abhängigkeiten

#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>So entfernen Sie eine Abhängigkeit für eine Funktion in der Projektmappe

1. Erweitern Sie in der Funktions-Designer die **Funktionsaktivierungsabhängigkeiten** Knoten, wählen Sie den Namen der Funktion, die Sie verwenden möchten, entfernen Sie aus, und wählen Sie dann die **entfernen** Schaltfläche.

## <a name="see-also"></a>Siehe auch
- [Erstellen von SharePoint-features](../sharepoint/creating-sharepoint-features.md)
- [Vorgehensweise: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Vorgehensweise: Hinzufügen und Entfernen von Elementen in SharePoint-Funktionen](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
