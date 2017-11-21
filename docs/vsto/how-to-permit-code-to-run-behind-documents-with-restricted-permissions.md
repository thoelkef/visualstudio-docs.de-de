---
title: "Vorgehensweise: Zulassen von Code für die Ausführung Hintergrund von Dokumenten mit eingeschränkten Berechtigungen | Microsoft Docs"
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
- Information Rights Management [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- IRM [Office development in Visual Studio]
- code [Office development in Visual Studio], running behind restricted documents
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
ms.assetid: d037eae5-cf83-4be0-85ba-05e9f7d570e1
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1d5ab02ea2eb2d34a82607b8f7fd4fbf3f02dd76
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Gewusst wie: Zulassen der Ausführung von Code im Hintergrund von Dokumenten mit eingeschränkten Berechtigungen
  Sie können die Information Rights Management (IRM)-Funktion von Microsoft Office verwenden, um Berechtigungen auf ein Dokument oder eine Arbeitsmappe zu beschränken. Standardmäßig ist der Code hinter einem eingeschränkten Microsoft Office Word-Dokument oder einer Microsoft Office Excel-Arbeitsmappe nicht zulässig, ausgeführt. Sie können die Standardeinstellung ändern, sodass Ihre Erweiterungen durch verwalteten Code auf das Objektmodell zugreifen können und Ihre Lösung funktioniert.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Sie müssen der Autor des Dokuments oder der Arbeitsmappe oder aber Vollzugriff auf die berechtigungseinstellungen ändern können.  
  
### <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Gestatten Sie Code Hintergrund von Dokumenten mit eingeschränkten Berechtigungen ausgeführt werden.  
  
1.  Öffnen Sie das Dokument oder die Arbeitsmappe in Word oder Excel.  
  
2.  Klicken Sie auf die **Datei** Registerkarte, zeigen Sie auf **vorbereiten**, zeigen Sie auf **Berechtigung einschränken**, und klicken Sie dann auf **Zugriffsbeschränkung**.  
  
    > [!NOTE]  
    >  Bei der ersten Verwendung werden Sie aufgefordert, den Windows Rights Management-Client installieren. Nachdem Sie den Client installieren, müssen Sie die Schritte wiederholen.  
  
3.  In der **Berechtigung** wählen Sie im Dialogfeld **Zugriffsberechtigung auf dieses Dokument einschränken**, und klicken Sie dann auf **Weitere Optionen**.  
  
4.  Klicken Sie unter **zusätzliche Berechtigungen für Benutzer**Option **programmgesteuerten Zugriff auf Inhalte**.  
  
 Word oder Excel ermöglicht den programmgesteuerten Zugriff auf das Objektmodell.  
  
## <a name="see-also"></a>Siehe auch  
 [Information Rights Management und Erweiterungen – Übersicht von verwaltetem Code](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Dokumentschutz in Projektmappen auf Dokumentebene](../vsto/document-protection-in-document-level-solutions.md)   
 [Kennwortschutz für Office-Dokumente](../vsto/password-protection-on-office-documents.md)   
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)   
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)  
  
  