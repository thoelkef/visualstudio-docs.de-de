---
title: "Die zum Erstellen des Projekts verwendete Arbeitsmappe enth&#228;lt ActiveX-Steuerelemente, die vom Designer nicht geladen werden k&#246;nnen. | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.SelectDocWizard.ContainsActiveXControls"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 91e9c6ee-7543-41e3-be0c-6c000cfd32d1
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Die zum Erstellen des Projekts verwendete Arbeitsmappe enth&#228;lt ActiveX-Steuerelemente, die vom Designer nicht geladen werden k&#246;nnen.
  Dieser Fehler wird angezeigt, wenn Sie ein Steuerelement einem Word\-Dokument oder einem Excel\-Arbeitsblatt programmgesteuert hinzufügen, das Dokument oder die Arbeitsmappe speichern, und dann eine neue Lösung auf Dokumentebene basierend auf dem Dokument oder der Arbeitsmappe erstellen.  
  
 Informationen über den verwalteten Typ des Steuerelements wird nicht zusammen mit dem Dokument oder der Arbeitsmappe gespeichert.  Wenn Sie eine neue Lösung basierend auf diesem Dokument oder dieser Arbeitsmappe erstellen, hat Visual Studio nicht genügend Informationen, um das Steuerelement im Hostelement\-Designer zu laden.  
  
### So beheben Sie diesen Fehler  
  
1.  Öffnen Sie das Dokument oder die Arbeitsmappe.  
  
2.  Entfernen Sie die Steuerelemente, die zur Laufzeit hinzugefügt wurden.  Wählen Sie sie dazu im Dokument oder in der Arbeitsmappe aus, und drücken Sie die ENTF\-Taste.  
  
3.  Erstellen Sie eine Lösung auf Dokumentebene basierend auf dem Dokument oder der Arbeitsmappe.  
  
## Siehe auch  
 [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  