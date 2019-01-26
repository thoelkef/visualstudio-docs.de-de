---
title: 'Vorgehensweise: Führen Sie einen Bildlauf durch Datenbankdatensätze in einem Arbeitsblatt'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 47a95db3797592f4c8d55ffa72e0e7323d251378
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863603"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Vorgehensweise: Führen Sie einen Bildlauf durch Datenbankdatensätze in einem Arbeitsblatt
  Das folgende Verfahren zeigt, wie den Designer verwendet, um ein einzelnes Feld aus einer Datenbanktabelle in einem Microsoft Office Excel-Arbeitsblatt mit Steuerelementen angezeigt wird, können dem Benutzer einen Bildlauf durch alle Datensätze durchführen, wird.  
  
 Sie können den Designer nur in Projekten auf Dokumentebene verwenden. Sie können jedoch auch Hinzufügen von Steuerelementen und binden diese an Daten programmgesteuert zur Laufzeit. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Einfache Datenbindung in VSTO-Add-in-Projekt](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="to-scroll-through-database-records-in-a-worksheet"></a>Scrollen Sie durch Datenbankdatensätze in einem Arbeitsblatt  
  
1.  Öffnen Sie ein Excel-Anwendungsprojekt in Visual Studio.  
  
2.  Öffnen der **Datenquellen** Fenster, und erstellen Sie eine Datenquelle aus der Datenbank. Weitere Informationen finden Sie unter [neue Verbindungen hinzufügen](../data-tools/add-new-connections.md).  
  
3.  Erweitern Sie die Tabelle, die die Daten enthält, die Sie anzeigen möchten, und wählen Sie die angegebene Spalte.  
  
4.  Öffnen Sie die Liste der Steuerelemente und wählen Sie **NamedRange**.  
  
5.  Ziehen Sie die <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement auf die Zelle, in denen die Daten angezeigt werden sollen.  
  
6.  Von der **Windows Forms** Registerkarte die **Toolbox**, Hinzufügen einer <xref:System.Windows.Forms.BindingNavigator> steuern, in das Arbeitsblatt, und richten Sie die Steuerelemente, die Sie verwenden möchten. Weitere Informationen finden Sie unter [Übersicht über das BindingNavigator-Steuerelement &#40;Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)  
