---
title: Source Control Entwurfsentscheidungen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4c1a512e104a092ae98ac86dc5e731fd1732aa33
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-design-decisions"></a>Entwurfsentscheidungen für Datenquellen-Steuerelement
Die folgenden entwurfsentscheidungen für Projekte berücksichtigen Sie beim Implementieren des Datenquellen-Steuerelements.  
  
## <a name="will-information-be-shared-or-private"></a>Werden Informationen freigegeben oder privat sein?  
 Die wichtigsten entwurfsentscheidung, die Sie vornehmen können ist, welche Informationen freigegeben werden kann und was privat ist. Beispielsweise ist die Liste der Dateien für das Projekt freigegeben, aber in dieser Liste der Dateien, einige möchten Benutzer ggf. private Dateien haben. Compilereinstellungen gelten, aber das Startprojekt ist im Allgemeinen privat. Einstellungen werden ausschließlich freigegebene, mit einer Außerkraftsetzung freigegebenen oder rein private. Programmbedingt private Elemente wie z. B. Lösung Benutzeroptionen (.suo)-Dateien nicht in die eingecheckt werden [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]. Achten Sie darauf, dass Sie zum Speichern der private Informationen im privaten Dateien wie z. B. die SUO-Datei oder einer bestimmten privaten-Datei, die Sie, z. B. Erstellen einer. csproj.user-Datei für Visual c# oder einer. vbproj.user-Datei für Visual Basic.  
  
 Diese Entscheidung ist nicht vollständig und kann auf einer Basis Element-vorgenommen werden.  
  
## <a name="will-the-project-include-special-files"></a>Wird das Projekt spezielle Dateien enthalten?  
 Eine andere wichtige entwurfsentscheidung ist, ob die Projektstruktur spezielle Dateien verwendet. Spezielle Dateien sind ausgeblendete Dateien, die die Dateien zugrunde liegen, die sichtbar im Projektmappen-Explorer und in das Einchecken und Auschecken Dialogfelder sind. Wenn Sie spezielle Dateien verwenden, beachten Sie Folgendes:  
  
1.  Ordnen Sie keine spezielle Dateien den Stammknoten des Projekts – d. h. mit dem Projekt die Datei selbst. Die Projektdatei, muss es sich um eine einzelne Datei sein.  
  
2.  Wenn spezielle Dateien hinzugefügt, entfernt oder umbenannt in einem Projekt auf die entsprechende <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> Ereignisse ausgelöst werden müssen, wobei das Flag festgelegt, der angibt, die Dateien sind spezielle Dateien. Diese Ereignisse werden von der Umgebung als Antwort auf das Projekt, das Aufrufen der entsprechenden aufgerufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Methoden.  
  
3.  Wenn das Projekt oder die-Editor aufruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> für eine Datei mit dieser Datei verknüpften speziellen Dateien werden nicht automatisch ausgecheckt. Übergeben Sie die speziellen Dateien im zusammen mit der übergeordneten Datei. Die Umgebung erkennt die Beziehung zwischen alle Dateien, die übergeben werden und entsprechend der speziellen Dateien in der Benutzeroberfläche Auschecken ausblenden.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Unterstützen der Quellcodeverwaltung](../../extensibility/internals/supporting-source-control.md)