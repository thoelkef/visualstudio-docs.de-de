---
title: Die zum Erstellen des Projekts verwendete Arbeitsmappe enthält ActiveX-Steuerelemente, die vom Designer nicht geladen werden können.
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9d47ee32f23ca0eb856b2a8f618d60fae552a027
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693070"
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>Die zum Erstellen des Projekts verwendete Arbeitsmappe enthält ActiveX-Steuerelemente, die vom Designer nicht geladen werden können.
  Dieser Fehler wird angezeigt, wenn Sie ein Steuerelement einem Word-Dokument oder einem Excel-Arbeitsblatt programmgesteuert hinzufügen, das Dokument oder die Arbeitsmappe speichern, und dann eine neue Lösung auf Dokumentebene basierend auf dem Dokument oder der Arbeitsmappe erstellen.  
  
 Informationen über den verwalteten Typ des Steuerelements wird nicht zusammen mit dem Dokument oder der Arbeitsmappe gespeichert. Wenn Sie eine neue Lösung basierend auf diesem Dokument oder dieser Arbeitsmappe erstellen, hat Visual Studio nicht genügend Informationen, um das Steuerelement im Hostelement-Designer zu laden.  
  
## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1.  Öffnen Sie das Dokument oder die Arbeitsmappe.  
  
2.  Entfernen Sie die Steuerelemente, die zur Laufzeit hinzugefügt wurden. Hierzu können Sie durch Auswahl in das Dokument oder die Arbeitsmappe und drücken die **löschen** Schlüssel.  
  
3.  Erstellen Sie eine Lösung auf Dokumentebene basierend auf dem Dokument oder der Arbeitsmappe.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  