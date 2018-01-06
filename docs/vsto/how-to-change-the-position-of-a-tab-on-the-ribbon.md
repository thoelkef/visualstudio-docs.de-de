---
title: "Vorgehensweise: Ändern der Position einer Registerkarte auf dem Menüband | Microsoft Docs"
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
helpviewer_keywords: Ribbon [Office development in Visual Studio], tabs
ms.assetid: 3f0906e3-9708-4136-ac49-986bc4c92ea4
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 196b16ba28ee5fa590c54dee89dcd65978f2ecd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Gewusst wie: Ändern der Position einer Registerkarte im Menüband
  Sie können die Reihenfolge von benutzerdefinierten Registerkarten auf einem Menüband ändern, indem Sie mit der **Registerkartenauflistungs-Editor**. Benutzerdefinierte Registerkarten können vor oder nach einer integrierten Registerkarte auf dem Menüband angeordnet werden. Eine integrierte Registerkarte ist eine Registerkarte, die sich bereits auf dem Menüband einer Microsoft Office-Anwendung befindet. Z. B. die **Daten** Registerkarte ist eine integrierte Registerkarte in Excel.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>So ändern Sie die Reihenfolge der Registerkarten auf dem Menüband  
  
1.  Wählen Sie in der Menüband-Codedatei (VB- oder CS-Datei) **Projektmappen-Explorer**.  
  
2.  Auf der **Ansicht** Menü klicken Sie auf **Designer**.  
  
3.  Mit der rechten Maustaste in der Menüband-Designer, und klicken Sie dann auf **Eigenschaften**.  
  
4.  In der **Eigenschaften** wählen die **Registerkarten** -Eigenschaft, und klicken Sie dann auf die Schaltfläche mit den Auslassungspunkten (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer Ellipse")).  
  
     Die **Registerkartenauflistungs-Editor** angezeigt wird.  
  
5.  In der **Registerkartenauflistungs-Editor**in der **Elemente** Liste, wählen Sie die Registerkarte, die Sie verschieben, und klicken Sie auf den nach-oben oder nach-unten-Pfeile, um die Aktivierreihenfolge ändern möchten.  
  
### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Um eine Registerkarte zu positionieren, vor oder nach einer integrierten Registerkarte auf dem Menüband  
  
1.  Wählen Sie im Menüband-Designer einer benutzerdefinierten Registerkarte ein.  
  
2.  In der **Eigenschaften** Fenster, erweitern Sie die **ControlId** -Eigenschaft, und stellen Sie dann sicher, dass der Wert des der **ControlIdType** Eigenschaft auf festgelegt ist **benutzerdefinierte**.  
  
3.  In der **Eigenschaften** Fenster, erweitern Sie die **Position** Eigenschaft.  
  
4.  Legen Sie die **PositionType** Eigenschaft auf den entsprechenden Wert:  
  
    -   **BeforeOfficeId** wird die Gruppe vor einer angegebenen integrierten Registerkarte.  
  
    -   **AfterOfficeId** wird die Gruppe hinter einer angegebenen integrierten Registerkarte.  
  
5.  Legen Sie die **OfficeId** Eigenschaft, um die Steuerelement-ID einer integrierten Registerkarte.  
  
     Eine Liste der Steuerelement-IDs, finden Sie unter [Office 2010 Help Files: Office Fluent User Interface Control Identifiers](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über das Menüband](../vsto/ribbon-overview.md)   
 [Menüband-Designer](../vsto/ribbon-designer.md)   
 [Menüband-XML](../vsto/ribbon-xml.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  