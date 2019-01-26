---
title: Dokumentschutz in Projektmappen auf Anwendungsebene
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b83715574ca9c5612e28f9097a1fcb378f298e1a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54862784"
---
# <a name="document-protection-in-document-level-solutions"></a>Dokumentschutz in Projektmappen auf Anwendungsebene
  Sie können die Schutzfunktionen von Microsoft Office Word und Microsoft Office Excel in Projekten auf Dokumentebene verwenden. Diese Features blockieren nicht autorisierte Benutzer Änderungen an geschützten Teile eines Dokuments.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Mit Excel können Sie Schutz aktivieren und deaktivieren, während die Arbeitsmappe im Designer geöffnet ist. Verwenden von Word, können Sie Schutz nur außerhalb der Designer aktivieren. Zur Laufzeit können Sie aktivieren oder Deaktivieren des Schutzes programmgesteuert für Word und Excel.  
  
 Dokumentschutz in einem Dokument aktiviert ist, die im Designer geöffnet ist, werden alle Steuerelemente aus entfernt die **Toolbox** oder deaktiviert ist, und Sie können keine Ziehen von der **Datenquellen** Fenster für das Dokument.  
  
## <a name="serverdocument-and-protected-documents"></a>ServerDocument und geschützte Dokumente  
 Wenn ein Dokument geschützt ist, kann nicht außerhalb des Dokuments aus das Datencache zugegriffen werden. Können keine der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> -Klasse zum Abrufen oder Bearbeiten von Daten, die in einem geschützten Dokument zwischengespeichert werden, oder verwenden Sie andere Methoden der <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> Klasse.  
  
## <a name="word-document-protection-in-the-designer"></a>Word-Dokument-Schutz im designer  
 Wenn Sie Schutz auf ein Word-Dokument oder eine Vorlage hinzufügen, während es in Visual Studio geöffnet ist, kann nicht gestartet werden, erzwingen der Protection im Designer. Das Dokument ist im Entwurfsmodus befindet, während es in Visual Studio geöffnet ist, und es muss werden im Ausführmodus bevor Sie beginnen können, erzwingen der Protection.  
  
 Wenn Sie ein Projekt, die ein vorhandenes Worddokument verwendet werden, das Schutz aktiviert ist erstellen, wird das Dokument jedoch beim Öffnen im Designer geschützt. Die geschützten Teile des Dokuments kann nicht bearbeitet werden, aber Sie können weiterhin Code im Code-Editor auf das Dokument zu automatisieren. Sie können nicht auch das Projekt erstellen, wenn der Schutz aktiviert ist, während das Dokument in Visual Studio geöffnet ist.  
  
 Sie können Schutz deaktivieren, während das Dokument im Designer geöffnet ist, damit Sie das Dokument bearbeiten und erstellen Sie das Projekt. Sie können keine Schutz für die Kopie im Designer deaktivieren, während des Debuggens; das Dokument, das während des Debuggens geöffnet wird, wird eine separate Kopie aus dem geöffneten im Designer (befindet sich die Ausgabekopie in die *\bin* Verzeichnis in Visual Basic und die *\bin\debug* Verzeichnis für C# ).  
  
 Sie können Schutz für die Kopie des Dokuments ermöglichen, die im Designer geöffnet wird, durch Schließen des Projekts in Visual Studio, öffnen die Kopie des Dokuments, das in das Projektverzeichnis ist und den Schutz aktivieren.  
  
## <a name="enforce-word-document-protection-on-build"></a>Erzwingen von Word-Dokument-Schutz für build  
 Visual Studio startet das Erzwingen der Protection für Word-Dokumenten und Vorlagen während des Buildprozesses, damit der Schutz aktiviert wird, wenn das Dokument für das Debuggen wird geöffnet. Das Dokument ist mit einem leeren Kennwort geschützt.  
  
 Schutz wird aktiviert während des Buildvorgangs also, wenn Code im Dokument <xref:Microsoft.Office.Tools.Word.Document.Startup> Ereignis, das möglicherweise Ausnahmen verursacht, oder ändern Sie das Verhalten der Anwendung, diesen Code richtig gedebuggt werden kann. Wenn Sie Schutz aktivieren, nachdem das Dokument geöffnet ist, kann nicht Code für die Initialisierung debuggt oder getestet werden.  
  
## <a name="setting-the-password"></a>Festlegen des Kennworts  
 Visual Studio automatisch Schutz aktiviert, jedoch kein Kennwort in der Standardeinstellung bietet. Wenn Sie den Dokumentschutz, ein Kennwort verwenden möchten, müssen Sie es hinzufügen, bevor Sie die Projektmappe bereitstellen. Durch Hinzufügen eines Kennworts, können Sie autorisierte Benutzern, die den Schutz aufheben können. ohne Kennwort kann nicht einfach Schutz entfernt werden. Weitere Informationen zum Festlegen eines Kennworts finden Sie Hilfe in der jeweiligen Anwendung.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes Schützen von Dokumenten und Teilen von Dokumenten](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)   
 [Verwaltung von Informationsrechten und Erweiterungen für verwalteten code](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Kennwortschutz für Office-Dokumente](../vsto/password-protection-on-office-documents.md)   
 [Vorgehensweise: Zulassen Sie Code Hintergrund von Dokumenten mit eingeschränkten Berechtigungen ausgeführt werden zu.](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)  
