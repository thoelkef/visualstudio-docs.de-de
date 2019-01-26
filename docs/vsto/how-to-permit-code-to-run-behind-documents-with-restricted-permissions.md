---
title: 'Vorgehensweise: Zulassen Sie Code Hintergrund von Dokumenten mit eingeschränkten Berechtigungen ausgeführt werden zu.'
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6030165e7b24bdba5c7fa6e223b915e5cf4c85c8
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870255"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Vorgehensweise: Zulassen Sie Code Hintergrund von Dokumenten mit eingeschränkten Berechtigungen ausgeführt werden zu.
  Sie können das Feature (Information Rights Management, IRM) von Microsoft Office verwenden, um Berechtigungen auf ein Dokument oder eine Arbeitsmappe zu beschränken. Standardmäßig ist der Code hinter einem eingeschränkten Microsoft Office Word-Dokument oder einer Microsoft Office Excel-Arbeitsmappe nicht zulässig, ausgeführt wird. Sie können die Standardeinstellung ändern, so, dass Ihre Erweiterungen durch verwalteten Code auf das Objektmodell zugreifen können und Ihre Lösung funktioniert.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Sie müssen der Autor des Dokuments oder der Arbeitsmappe oder verfügen über Vollzugriff auf die berechtigungseinstellungen ändern können.  
  
## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Um zuzulassen Code Hintergrund von Dokumenten mit eingeschränkten Berechtigungen ausgeführt werden.  
  
1. Öffnen Sie das Dokument oder die Arbeitsmappe in Word oder Excel.  
  
2. Klicken Sie auf die **Datei** Registerkarte, zeigen Sie auf **vorbereiten**, zeigen Sie auf **Berechtigung einschränken**, und klicken Sie dann auf **eingeschränkten Zugriff**.  
  
   > [!NOTE]  
   >  Bei der ersten Verwendung werden Sie aufgefordert, den Windows Rights Management-Client installieren. Nachdem Sie den Client installieren, müssen Sie die Schritte wiederholen.  
  
3. In der **Berechtigung** wählen Sie im Dialogfeld **Zugriffsberechtigung auf dieses Dokument einschränken**, und klicken Sie dann auf **Weitere Optionen**.  
  
4. Klicken Sie unter **zusätzliche Berechtigungen für Benutzer**Option **programmgesteuerten Zugriff auf Inhalt**.  
  
   Word oder Excel ermöglicht den programmgesteuerten Zugriff auf das Objektmodell.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwaltung von Informationsrechten und Erweiterungen für verwalteten code](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Dokumentschutz in Projektmappen auf Anwendungsebene](../vsto/document-protection-in-document-level-solutions.md)   
 [Kennwortschutz für Office-Dokumente](../vsto/password-protection-on-office-documents.md)   
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)   
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)  
