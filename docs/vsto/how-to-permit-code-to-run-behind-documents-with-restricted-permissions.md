---
title: 'Vorgehensweise: Zulassen von Code für die Ausführung Hintergrund von Dokumenten mit eingeschränkten Berechtigungen | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: eb5b9421bd6d0228a93ba7ba7516c9ebc7b7c761
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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
  
  