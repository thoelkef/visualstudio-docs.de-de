---
title: "Vorgehensweise: Führen Sie einen Bildlauf durch Datenbankdatensätze in einem Arbeitsblatt | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f7e6ea8269401a8b026da2562eff96e50820e0a0
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Gewusst wie: Ausführen eines Bildlaufs durch Datenbankdatensätze in einem Arbeitsblatt
  Das folgende Verfahren veranschaulicht, wie der Designer verwenden, um ein einzelnes Feld aus einer Datenbanktabelle in einem Microsoft Office Excel-Arbeitsblatt mit Steuerelementen anzuzeigen, die der Benutzer einen Bildlauf durch alle Datensätze ermöglichen.  
  
 Sie können den Designer nur in Projekten auf Dokumentebene verwenden. Sie können jedoch auch Steuerelemente hinzufügen und diese zur Laufzeit programmgesteuert an Daten binden. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: einfache Datenbindung in einem VSTO-add-in-Projekt](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
### <a name="to-scroll-through-database-records-in-a-worksheet"></a>Einen Bildlauf durch Datenbankdatensätze in einem Arbeitsblatt  
  
1.  Öffnen Sie ein Projekt für Excel-Anwendung in Visual Studio.  
  
2.  Öffnen der **Datenquellen** Fenster, und erstellen Sie eine Datenquelle aus der Datenbank. Weitere Informationen finden Sie unter [neue Verbindungen hinzufügen](../data-tools/add-new-connections.md).  
  
3.  Erweitern Sie die Tabelle, die die Daten enthält, die Sie anzeigen möchten, und wählen Sie die spezifische Spalte.  
  
4.  Öffnen Sie die Liste der Steuerelemente, und wählen **NamedRange**.  
  
5.  Ziehen Sie die <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement auf die Zelle, in dem die Daten angezeigt werden sollen.  
  
6.  Aus der **Windows Forms** auf der Registerkarte die **Toolbox**, Hinzufügen einer <xref:System.Windows.Forms.BindingNavigator> -Steuerelement auf das Arbeitsblatt, und richten Sie die Steuerelemente, die Sie verwenden möchten. Weitere Informationen finden Sie unter [Übersicht über das BindingNavigator-Steuerelement &#40; Windows Forms &#41; ](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  