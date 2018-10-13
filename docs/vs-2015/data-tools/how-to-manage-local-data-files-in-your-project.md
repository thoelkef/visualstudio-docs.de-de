---
title: 'Vorgehensweise: Verwalten von lokalen Datendateien im Projekt | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.data.LocalConnectionConverter
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- mdf files
- local data
- .mdb files
- .mdf files
- data [Visual Studio], local
- mdb files
ms.assetid: 3ffa1aa9-17e4-422c-a02f-09224828cdfc
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 16e2d38dda97bd8a7f130254b2f23be9f17e0ac4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49271374"
---
# <a name="how-to-manage-local-data-files-in-your-project"></a>Gewusst wie: Verwalten von lokalen Datendateien im Projekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine lokale Datenbankdatei kann als Datei in ein Projekt eingebunden werden. Beim erstmaligen Herstellen einer Verbindung mit einer lokalen Datenbankdatei, können Sie auswählen, erstellen Sie eine Kopie in Ihrem Projekt oder eine Verbindung mit der vorhandenen Datei am aktuellen Speicherort herstellen. Wenn Sie an die vorhandene Datei verbunden sind, wird sie in ihrem ursprünglichen Speicherort belassen. Wenn Sie die Datei in Ihr Projekt kopieren möchten, Visual Studio erstellt eine Kopie der Datei dem Projekt hinzugefügt und ändert die Verbindung auf die Kopie verweisen. Andere Verbindungen, z. B. in Server-Explorer werden ebenfalls geändert.  
  
 Die Standardeinstellung der Eigenschaft hängt von den Typ der Datenbankdatei, die Sie verwenden. Das Verhalten der **in Ausgabeverzeichnis kopieren** Eigenschaft gilt nicht für Webprojekte oder C++-Projekte.  
  
 Während der Entwicklung empfiehlt es sich um die Auswirkungen des Codes für die Datenbank anzuzeigen, ohne diese Änderungen dauerhaft. Sie können dies durch Einstellung der **in Ausgabeverzeichnis kopieren** -Eigenschaft der Datei auf "true". Jedes Mal, die das Projekt wird erstellt, oder Sie Drücken der Taste F5 wird die Datei im Ordner Bin kopiert und Änderungen an dieser Datei nicht auf die Datei im Stammordner des Projekts vorgenommen werden. Die Datenbankdatei im Stammordner des Projekts wird nur geändert, wenn Sie das Datenbankschema oder die Daten bearbeiten **Server-Explorer**, **Datenbank-Explorer** oder andere Toolfenster.  
  
 Die folgende Tabelle beschreibt die Einstellungen der **in Ausgabeverzeichnis kopieren** Eigenschaft.  
  
|Einstellung|Verhalten|  
|-------------|--------------|  
|**Kopieren, wenn neuer** (Standardeinstellung für SDF-Dateien)|Die Datenbankdatei wird kopiert, aus dem Projektverzeichnis in das **Bin** Verzeichnis das erste Mal das Projekt erstellt wird. Jedes Mal, die Sie das Projekt erstellen, das **Änderungsdatum** Eigenschaft der Dateien verglichen wird. Wenn die Datei im Projektordner neuer ist, wird Sie kopiert die **Bin** Ordner, und Ersetzen Sie dabei die Datei, die derzeit vorhanden ist. Wenn die Datei in die **Bin** Ordner neuer ist, werden keine Dateien kopiert. Mit dieser Einstellung werden alle zur Laufzeit vorgenommenen Änderungen an den Daten beibehalten, d. h., jedes Mal, wenn Sie die Anwendung ausführen und Änderungen an den Daten speichern, sind diese Änderungen beim nächsten Ausführen der Anwendung sichtbar. **Vorsicht:** nicht empfohlen, diese Option für MDB- oder MDF-Dateien. Die Datenbankdatei kann sogar geändert werden, wenn gar keine Änderungen an den Daten vorgenommen werden. Einfach Öffnen einer Verbindung einer Datendatei (z. B. durch Erweitern der **Tabellen** Knoten **Server-Explorer**) kann dann als neuer gekennzeichnet werden.|  
|**Immer kopieren** (Standardeinstellung für MDF- und MDB-Dateien)|Bei jedem Erstellen der Anwendung wird die Datenbankdatei aus dem Projektverzeichnis in das Verzeichnis "/bin" kopiert. Deshalb werden, wenn Sie die Anwendung erstellen und Änderungen an der Datei speichern, diese Änderungen überschrieben, wenn die ursprüngliche Datei das nächste Mal in das /bin-Verzeichnis kopiert wird.|  
|**Nicht kopieren**|Die Datei wird vom Projektsystem niemals kopiert oder überschrieben. Sie müssen die Datei manuell aus dem Projektverzeichnis in das Ausgabeverzeichnis kopieren, wenn Sie diese Einstellung verwenden.|  
  
## <a name="procedure"></a>Prozedur  
  
#### <a name="to-respond-to-the-local-database-file-dialog-box"></a>So reagieren Sie auf das Dialogfeld "Lokale Datenbankdatei"  
  
-   Klicken Sie auf **Ja** Wenn Sie Visual Studio die Datenbankdatei in Ihr Projekt kopieren und die Verbindung so zeigen Sie auf die Kopie in Ihrem Projekt ändern möchten. Weitere Informationen zum Arbeiten mit Datenbankdateien im Projekt finden Sie unter [Übersicht über lokale Daten](../data-tools/local-data-overview.md).  
  
-   Klicken Sie auf **keine** , wenn Sie nicht über Visual Studio die Datenbankdatei in Ihr Projekt kopieren möchten. Stattdessen zeigt die Verbindung auf die Datei am ursprünglichen Speicherort, und die Datenbankdatei wird dem Projekt nicht als Datei hinzugefügt.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Verbinden mit Daten in einer lokalen Datenbankdatei (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Herstellen einer Verbindung mit Daten in einer Access-Datenbank (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)