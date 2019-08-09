---
title: Dokument Schutz in Projektmappen auf Dokument Ebene
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
ms.openlocfilehash: 5a894f1e0fb9d5e9d55f46c442bc975de0bd900d
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68872068"
---
# <a name="document-protection-in-document-level-solutions"></a>Dokument Schutz in Projektmappen auf Dokument Ebene
  Sie können die Schutz Features von Microsoft Office Word und Microsoft Office Excel in Projekten auf Dokument Ebene verwenden. Diese Features blockieren nicht autorisierte Benutzer daran, Änderungen an geschützten Teilen eines Dokuments vorzunehmen.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Wenn Sie Excel verwenden, können Sie den Schutz aktivieren und deaktivieren, während die Arbeitsmappe im Designer geöffnet ist. Mit Word können Sie den Schutz nur außerhalb des Designers aktivieren. Zur Laufzeit können Sie den Schutz für Word und Excel Programm gesteuert aktivieren oder deaktivieren.

 Wenn der Dokument Schutz für ein Dokument aktiviert ist, das im Designer geöffnet ist, werden alle Steuerelemente aus der **Toolbox** entfernt oder sind nicht verfügbar, und Sie können nichts aus dem **Datenquellen** Fenster in das Dokument ziehen.

## <a name="serverdocument-and-protected-documents"></a>ServerDocument und geschützte Dokumente
 Wenn ein Dokument geschützt ist, kann nicht von außerhalb des Dokuments auf den Daten Cache zugegriffen werden. Sie können die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> -Klasse nicht verwenden, um Daten abzurufen oder zu bearbeiten, die in einem geschützten Dokument zwischengespeichert sind, <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> oder andere Methoden der-Klasse zu verwenden.

## <a name="word-document-protection-in-the-designer"></a>Schutz von Word-Dokumenten im Designer
 Wenn Sie den Schutz einem Word-Dokument oder einer Vorlage hinzufügen, während es in Visual Studio geöffnet ist, können Sie nicht mit der Erzwingung des Schutzes im Designer beginnen. Das Dokument befindet sich im Entwurfs Modus, während es in Visual Studio geöffnet ist, und es muss sich im Testmodus befinden, bevor Sie mit der Erzwingung des Schutzes beginnen können.

 Wenn Sie jedoch ein Projekt erstellen, das ein vorhandenes Word-Dokument verwendet, für das der Schutz aktiviert ist, wird das Dokument geschützt, während es im Designer geöffnet wird. Die geschützten Teile des Dokuments können nicht bearbeitet werden, aber Sie können weiterhin Code im Code-Editor schreiben, um das Dokument zu automatisieren. Sie können das Projekt auch nicht erstellen, wenn der Schutz aktiviert ist, während das Dokument in Visual Studio geöffnet ist.

 Sie können den Schutz deaktivieren, während das Dokument im Designer geöffnet ist, sodass Sie das Dokument bearbeiten und das Projekt erstellen können. Während des Debuggens können Sie den Schutz für die Kopie im Designer nicht deaktivieren. das Dokument, das während des Debuggens geöffnet wird, ist eine separate Kopie, die im Designer geöffnet ist (die Ausgabe Kopie wird im Verzeichnis " *\bin* " für Visual Basic und das Verzeichnis " C# *\bin\debug* " für) gespeichert.

 Sie können den Schutz für die Kopie des Dokuments aktivieren, das im Designer geöffnet wird, indem Sie das Projekt in Visual Studio schließen, die Kopie des Dokuments öffnen, das sich im Projektverzeichnis befindet, und den Schutz aktivieren.

## <a name="enforce-word-document-protection-on-build"></a>Erzwingen des Schutzes von Word-Dokumenten für den Build
 Visual Studio beginnt, den Schutz für Word-Dokumente und-Vorlagen während des Buildprozesses zu erzwingen, sodass der Schutz aktiviert wird, wenn das Dokument zum Debuggen geöffnet wird Das Dokument ist durch ein leeres Kennwort geschützt.

 Der Schutz wird während des Buildvorgangs aktiviert, sodass dieser Code korrekt <xref:Microsoft.Office.Tools.Word.Document.Startup> debuggt werden kann, wenn im Dokument Ereignis Code vorhanden ist, der Ausnahmen verursachen oder das Verhalten der Anwendung ändern kann. Wenn Sie den Schutz aktivieren, nachdem das Dokument geöffnet wurde, kann der Initialisierungs Code nicht deentschlbelt oder getestet werden.

## <a name="setting-the-password"></a>Festlegen des Kennworts
 Visual Studio aktiviert automatisch den Schutz, aber standardmäßig wird kein Kennwort bereitstellt. Wenn Sie möchten, dass der Dokument Schutz ein Kennwort hat, müssen Sie es vor dem Bereitstellen der Lösung hinzufügen. Durch das Hinzufügen eines Kennworts können autorisierte Benutzer den Schutz aus dem Dokument entfernen. ohne Kennwort kann der Schutz nicht einfach entfernt werden. Ausführliche Informationen zum Festlegen eines Kennworts finden Sie in der Hilfe zu einer bestimmten Office-Anwendung.

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Programm gesteuertes schützen von Dokumenten und Teilen von Dokumenten](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)
- [Office-Entwicklungs Beispiele und Exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)
- [Übersicht über Verwaltung von Informationsrechten und Erweiterungen von verwalteten Code](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Kenn Wort Schutz für Office-Dokumente](../vsto/password-protection-on-office-documents.md)
- [Vorgehensweise: Zulassen, dass Code hinter Dokumenten mit eingeschränkten Berechtigungen ausgeführt wird](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)
