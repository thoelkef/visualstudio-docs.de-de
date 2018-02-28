---
title: "Vorgehensweise: Hinzufügen und Entfernen von Funktionsabhängigkeiten | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 6e74ac8cef88319a54df0c08cd91fb2654d390cb
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Gewusst wie: Hinzufügen und Entfernen von Funktionsabhängigkeiten
  Die SharePoint-Funktion kann auf andere Funktionen für Funktionen oder Daten abhängen. In diesen Fällen können Sie diese andere Funktionen als Abhängigkeiten für Ihre Funktion markieren. Auf diese Weise wird sichergestellt, dass die SharePoint-Server, dass die abhängigen Funktionen aktiviert sind, bevor die Funktion aktiviert ist.  
  
## <a name="adding-dependencies"></a>Hinzufügen von Abhängigkeiten  
 Sie können andere Funktionen als Abhängigkeiten in der Projektmappe hinzufügen. Auf diese Weise können Sie sicherstellen, dass erforderliche Features installiert und aktiviert werden, bevor die Funktion installiert ist.  
  
#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Hinzufügen eine Abhängigkeit auf eine Funktion in der Projektmappe  
  
1.  Die Funktions-Designer öffnen, erweitern Sie die **Aktivierung Featureabhängigkeiten** Knoten, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
2.  In der **hinzufügen Featureabhängigkeiten Aktivierung** Dialogfeld Wählen Sie die **fügen eine Abhängigkeit auf Funktionen in der Projektmappe** Optionsfeld, wählen Sie den Titel der Funktion, die Sie als eine Abhängigkeit hinzufügen möchten und klicken Sie dann Wählen Sie die **hinzufügen** Schaltfläche.  
  
     Sie können mehr als eine Funktion hinzufügen, indem Sie mehrere Titel beim Auswählen der STRG-Taste auswählen.  
  
## <a name="adding-custom-dependencies"></a>Hinzufügen von benutzerdefinierten Abhängigkeiten  
 Hinzufügen von Funktionen, die bereits bereitgestellt sind auf einem SharePoint-Server als Abhängigkeit. Auf diese Weise überprüft der SharePoint-Aktivierungsprozess, um sicherzustellen, dass alle abhängigen Features aktiviert werden, bevor die Funktion installiert ist.  
  
#### <a name="to-add-a-dependency-by-the-feature-id"></a>Hinzufügen eine Abhängigkeit von der Funktions-ID  
  
1.  Die Funktions-Designer öffnen, erweitern Sie die **Aktivierung Featureabhängigkeiten** Knoten, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
2.  In der **hinzufügen Featureabhängigkeiten Aktivierung** Dialogfeld Wählen Sie die **fügen Sie eine benutzerdefinierte Abhängigkeit** Optionsfeld.  
  
3.  In der **Funktions-ID** Text Geben Sie die GUID für die Funktion, die Sie verwenden möchten, als Abhängigkeit Aktivierung zu markieren, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
## <a name="editing-custom-dependencies"></a>Bearbeiten von benutzerdefinierten Abhängigkeiten  
 Sie können benutzerdefinierte Abhängigkeiten bearbeiten, die Sie zuvor hinzugefügt haben. Abhängige Funktionen, die in der Projektmappe können nur entfernt werden, jedoch nicht mehr bearbeitet.  
  
#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>So ändern Sie eine Abhängigkeit auf eine Funktion in der Projektmappe  
  
1.  Öffnen des Funktions-Designers, und erweitern Sie dann die **Aktivierung Featureabhängigkeiten** Knoten.  
  
2.  Wählen Sie den Namen der Funktion, die Sie bearbeiten möchten, und wählen Sie dann die **bearbeiten** Schaltfläche.  
  
3.  In der **Bearbeiten benutzerdefinierter Aktivierung Funktionsabhängigkeit** (Dialogfeld), ändern Sie den Titel, Funktions-ID oder Beschreibung, und wählen Sie dann die **Absenden** Schaltfläche.  
  
## <a name="removing-dependencies"></a>Entfernen von Abhängigkeiten  
  
#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>So entfernen Sie eine Abhängigkeit auf eine Funktion in der Projektmappe  
  
1.  Erweitern Sie in der Funktions-Designer die **Aktivierung Featureabhängigkeiten** Knoten, wählen Sie den Namen der Funktion, die Sie entfernen möchten, und wählen Sie dann die **entfernen** Schaltfläche.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von SharePoint-Funktionen](../sharepoint/creating-sharepoint-features.md)   
 [Vorgehensweise: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Vorgehensweise: Hinzufügen und Entfernen von Elementen in SharePoint-Funktionen](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  