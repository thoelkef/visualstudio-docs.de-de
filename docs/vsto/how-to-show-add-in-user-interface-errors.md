---
title: 'Vorgehensweise: Anzeigen von Add-In-Benutzeroberflächenfehlern | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 795578d6a168dff5fee259a90abac83fa7788121
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Gewusst wie: Anzeigen von Add-In-Benutzeroberflächenfehlern
  Wenn ein VSTO-Add-In erfolglos versucht, die Microsoft Office-Benutzeroberfläche zu verändern, wird standardmäßig keine Fehlermeldung angezeigt. Sie können Microsoft Office-Anwendungen aber so konfigurieren, dass Meldungen für Fehler angezeigt werden, die sich auf die Benutzeroberfläche beziehen. Mit diesen Meldungen können Sie feststellen, warum ein Menüband nicht angezeigt wird oder warum ein Menüband angezeigt wird, aber keine Steuerelemente.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-show-vsto-add-in-user-interface-errors"></a>So zeigen Sie VSTO-Add-In-Benutzeroberflächenfehler an  
  
1.  Starten Sie die Anwendung.  
  
2.  Klicken Sie auf die Registerkarte **Datei** .  
  
3.  Klicken Sie auf **Optionen**.  
  
4.  Klicken Sie im Bereich "Kategorien" auf **Erweitert**.  
  
5.  Wählen Sie im Detailbereich die Option **VSTO-Add-In-Benutzeroberflächenfehler anzeigen**aus, und klicken Sie dann auf **OK**.  
  
    > [!NOTE]  
    >  Für Outlook befindet sich das Kontrollkästchen **VSTO-Add-In-Benutzeroberflächenfehler anzeigen** im Abschnitt **Entwickler** des Detailbereichs. Für andere Anwendungen befindet sich das Kontrollkästchen im Abschnitt **Allgemein** des Detailbereichs.  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)   
 [Übersicht über das Menüband](../vsto/ribbon-overview.md)   
 [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)  
  
  