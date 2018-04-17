---
title: Dokumentschutz in Projektmappen auf Dokumentebene | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 546a74179b8bdf52541d771809426b5e4aec3e45
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="document-protection-in-document-level-solutions"></a>Dokumentschutz in Projektmappen auf Dokumentebene
  Sie können die Schutzfunktionen von Microsoft Office Word und Microsoft Office Excel in Projekten auf Dokumentebene verwenden. Diese Funktionen Sperren nicht autorisierte Benutzer Änderungen an geschützten Teile eines Dokuments.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Verwenden Excel, können Sie Schutz auf Aktivieren und deaktivieren, während die Arbeitsmappe im Designer geöffnet ist. Mit Word können Sie Schutz nur außerhalb des Designers aktivieren. Zur Laufzeit können Sie aktivieren oder deaktivieren Sie den Schutz programmgesteuert zu Word- und Excel.  
  
 Dokumentschutz für ein Dokument aktiviert ist, die im Designer geöffnet ist, werden alle Steuerelemente aus entfernt die **Toolbox** oder sind nicht verfügbar ist, und Sie nicht alles aus Ziehen der **Datenquellen** Fenster, um das Dokument.  
  
## <a name="serverdocument-and-protected-documents"></a>ServerDocument und geschützte Dokumente  
 Wenn ein Dokument geschützt ist, kann der Datencache außerhalb des Dokuments aus zugegriffen werden. Können Sie keine der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> -Klasse zum Abrufen oder Bearbeiten von Daten, die in ein geschütztes Dokument zwischengespeichert werden, oder verwenden Sie andere Methoden der <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> Klasse.  
  
## <a name="word-document-protection-in-the-designer"></a>Word-Dokument-Schutz im Designer  
 Wenn Sie Schutz auf einem Word-Dokument oder einer Vorlage hinzufügen, während sie in Visual Studio geöffnet ist, können nicht Sie mit der Erzwingung des Schutzes im Designer beginnen. Das Dokument ist in den Entwurfsmodus zu wechseln, während es in Visual Studio geöffnet ist, und es muss werden im Ausführmodus bevor Sie beginnen können, erzwingen von Schutz.  
  
 Wenn Sie ein Projekt erstellen, ein vorhandenes Worddokument verwendet, das Schutz aktiviert ist, ist das Dokument beim Öffnen im Designer geschützt. Die geschützten Teile des Dokuments können nicht bearbeitet werden, aber Sie können weiterhin Code im Code-Editor, um das Dokument zu automatisieren. Sie können nicht auch das Projekt erstellen, wenn der Schutz aktiviert ist, während das Dokument im Visual Studio geöffnet ist.  
  
 Sie können Schutz deaktivieren, während das Dokument im Designer geöffnet ist, damit Sie das Dokument bearbeiten können, und erstellen Sie das Projekt. Sie können Schutz für die Kopie im Designer deaktivieren, während des Debuggens; das Dokument, das während des Debuggens öffnet ist eine separate Kopie von einer Open im Designer (die Ausgabekopie wird in das Verzeichnis "\bin" für Visual Basic und c# im Verzeichnis \bin\debug gespeichert).  
  
 Sie können Schutz für die Kopie des Dokuments aktivieren, die im Designer geöffnet ist, schließen das Projekt in Visual Studio und öffnen die Kopie des Dokuments, das sich im Projektverzeichnis Schutz einschalten.  
  
## <a name="enforcing-word-document-protection-on-build"></a>Erzwingen von Word-Dokument-Schutz auf Build  
 Visual Studio erzwingt den Schutz für Word-Dokumenten und Vorlagen während des Buildprozesses, damit der Schutz aktiviert ist, beim Öffnen des Dokuments zum Debuggen. Das Dokument ist mit einem leeren Kennwort geschützt.  
  
 Ist der Schutz aktiviert während des Buildvorgangs also, wenn Code im Dokument <xref:Microsoft.Office.Tools.Word.Document.Startup> Ereignis, das möglicherweise Ausnahmen verursacht, oder ändern Sie das Verhalten der Anwendung, diesen Code richtig gedebuggt werden kann. Wenn Sie Schutz aktivieren, nachdem das Dokument geöffnet ist, kann nicht Initialisierungscode gedebuggt oder getestet werden.  
  
## <a name="setting-the-password"></a>Festlegen des Kennworts  
 Visual Studio automatisch ermöglicht den Schutz, jedoch standardmäßig kein Kennwort bereitgestellt. Gegebenenfalls den Dokumentschutz Kennwort müssen Sie sie hinzufügen, bevor Sie die Projektmappe bereitstellen. Durch Hinzufügen eines Kennworts ermöglicht es Ihnen, können autorisierte Benutzer aus dem Dokument entfernen des Schutzes; ohne Kennwort kann nicht einfach Schutz entfernt werden. Weitere Informationen zum Festlegen eines Kennworts finden Sie Hilfe in der jeweiligen Anwendung.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes Schützen von Dokumenten und Dokumentteilen](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)   
 [Information Rights Management und Erweiterungen – Übersicht von verwaltetem Code](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Kennwortschutz für Office-Dokumente](../vsto/password-protection-on-office-documents.md)   
 [Vorgehensweise: Zulassen von Code für die Ausführung Hintergrund von Dokumenten mit eingeschränkten Berechtigungen](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)  
  
  