---
title: 'Vorgehensweise: Speichern und Öffnen von Dateien mit Codierung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Unicode, bi-directional language support
- files, encoding
- bi-directional language support, encoded files
- file encoding, bi-directional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b179637d9607db70aac415abd477da4a62852efe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49213784"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Gewusst wie: Speichern und Öffnen von Dateien mit Codierung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Dateien mit ausgewählter Zeichencodierung speichern, sodass bidirektionale Sprachen unterstützt werden. Sie können außerdem auch beim Öffnen einer Datei eine Codierung angeben, sodass Visual Studio die Datei korrekt anzeigt.  
  
### <a name="to-save-a-file-with-encoding"></a>So speichern Sie eine codierte Datei  
  
1.  Klicken Sie im Menü **Datei** auf **Datei speichern unter**, und klicken Sie dann neben der Schaltfläche **Speichern** auf die Dropdownschaltfläche.  
  
     Das Dialogfeld **Erweiterte Speicheroptionen** wird angezeigt.  
  
2.  Wählen Sie unter **Codierung** die gewünschte Codierung für diese Datei aus.  
  
3.  Optional können Sie unter **Zeilenenden** das Format für die Zeichen am Zeilenende auswählen.  
  
     Diese Option ist sehr praktisch, wenn Sie die Datei an Benutzer eines anderen Betriebssystems weitergeben möchten.  
  
     Wenn Sie mit einer Datei arbeiten möchten, von der Sie wissen, wie sie codiert wurde, können Sie in Visual Studio angeben, dass diese Codierung beim Öffnen verwendet werden soll. Welche Methode Sie verwenden, hängt davon ab, ob die Datei Teil des Projekts ist.  
  
### <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>So öffnen Sie eine codierte Datei, die Teil eines Projekts ist  
  
1.  Klicken Sie im **Projektmappen**-Explorer mit der rechten Maustaste auf die Datei, und wählen Sie **Öffnen mit** aus.  
  
2.  Wählen Sie im Dialogfeld **Öffnen mit** den Editor aus, mit dem die Datei geöffnet werden soll.  
  
     Viele der Editoren von Visual Studio, z. B. der Formular-Editor, erkennen die Codierung automatisch und öffnen die Datei dann entsprechend. Wenn Sie einen Editor verwenden, bei dem Sie eine Codierung auswählen können, wird das Dialogfeld **Codierung** angezeigt.  
  
3.  Wählen Sie in diesem Fall im Dialogfeld **Codierung** die vom Editor zu verwendende Codierung aus.  
  
### <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>So öffnen Sie eine codierte Datei, die nicht Teil eines Projekts ist  
  
1.  Zeigen Sie im Menü **Datei** auf **Öffnen**, wählen Sie **Datei** oder **Datei im Web** aus, und wählen Sie dann die zu öffnende Datei aus.  
  
2.  Klicken Sie neben der Schaltfläche **Öffnen** auf die Dropdownschaltfläche, und klicken Sie auf **Öffnen mit**.  
  
3.  Führen Sie die Schritte 2 und 3 der vorherigen Prozedur aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Codierung und die Globalisierung von Windows Forms](http://msdn.microsoft.com/library/22e8965d-a712-42b3-8167-3ee346bd70f9)   
 [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)

