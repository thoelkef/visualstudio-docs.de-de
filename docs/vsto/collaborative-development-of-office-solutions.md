---
title: Gemeinsame Entwicklung von Office-Projektmappen
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9b4d22c92bd180eb27f8ebb50e65b24d17a92e47
ms.sourcegitcommit: a715de2ba8c703f37aa2102567b1aa2c0f05a117
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53441547"
---
# <a name="collaborative-development-of-office-solutions"></a>Gemeinsame Entwicklung von Office-Projektmappen
  Mehrere Entwickler können auf einem Office-Projekt auf die gleiche Weise arbeiten, die sie an andere Visual Studio-Projekten arbeiten. Visual Studio findet die Microsoft Office-Installation auf jedem Computer, selbst wenn Office an verschiedenen Speicherorten installiert ist. Es gibt jedoch einige wichtige Punkte zu berücksichtigen.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="debug-properties-are-not-shared"></a>Debuggen von Eigenschaften werden nicht freigegeben.  
 In der Quellcodeverwaltung werden Debugeigenschaften nicht für mehrere Benutzer gemeinsam verwendet. Visual Basic und Visual C# Projekte speichern die Debugeigenschaften in einer benutzerspezifischen Datei (*ProjectName*. vbproj.user oder *ProjectName*. csproj.user), und diese Datei befindet sich nicht unter quellcodeverwaltung . Wenn mehrere Personen debuggen, muss jede Person die Debugeigenschaften manuell eingeben.  
  
 Wenn das Projekt auf einer Netzwerkfreigabe statt in der quellcodeverwaltung gespeichert ist, müssen einige zusätzliche Schritte ausgeführt werden, mit denen die zusammenarbeitenden Entwickler die Projektmappe öffnen, und Testen Sie die Assembly.  
  
## <a name="source-control-requires-checking-out-all-files"></a>Datenquellen-Steuerelement ist erforderlich, alle Dateien werden ausgecheckt  
 Wenn Sie die quellcodeverwaltung für Ihre Projekte verwenden, sollten Sie sehen Sie sich alle Dateien in einer Codedatei im **Projektmappen-Explorer** (z. B. die *ThisDocument*, *ThisWorkbook*, oder *ThisAddIn* Codedateien) jedes Mal, wenn Sie die Codedatei "" ändern, auch die Dateien, die standardmäßig ausgeblendet sind. Wenn Sie nur auf der obersten Ebene Codedatei Auschecken, können Ihre Änderungen verloren gehen.  
  
 Nachdem Sie Ihre Änderungen vornehmen, alle Dateien wieder eingecheckt. Weitere Informationen zu den ausgeblendeten Codedateien in Projekten, finden Sie unter [Office-Projekten in Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="security-for-informal-collaboration-on-a-network"></a>Sicherheit für die informelle Zusammenarbeit in einem Netzwerk  
 Für alle Projektmappen auf Anwendungsebene, die in einem Speicherort im Netzwerk befinden (z. B. \\ \\ *Servername*\\*Sharename*), muss der vollqualifizierte Speicherort hinzugefügt werden der Liste vertrauenswürdiger Ordner in der Microsoft Office-Anwendung, mit der Sie arbeiten werden. Wählen Sie die Option zum Einschließen der Unterverzeichnisse unter dem Hauptordner oder speziell Debuggen hinzufügen und Erstellen von Ordnern zur Liste vertrauenswürdiger Ordner. Weitere Informationen hierzu finden Sie unter [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md).  
  
 Die temporäre Zertifikate, die zum Zeitpunkt der Erstellung automatisch generiert werden, werden nicht durch Kennwörter gesichert. Die Zertifikate enthalten den Namen des Entwicklers Anmeldung und andere persönliche Informationen. Wenn Sie Anpassungen, die von temporären Zertifikaten signiert sind bereitstellen, anderen Benutzern Zugriff auf diese Informationen möglicherweise.  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)   
 [Erstellen von Office-Projektmappen](../vsto/building-office-solutions.md)  
  
  