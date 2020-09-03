---
title: 'Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b1b4e59e43a4a5aeb129464a34b96ef3f665e72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148868"
---
# <a name="walkthrough-creating-a-custom-editor"></a>Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die VSPackage-Projektvorlage kann einen einfachen benutzerdefinierten Editor in C++ erstellen.  Die VSPackage-Projektvorlage unterstützt nicht mehr c#-oder Visual Basic-Projekte. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>Die Projektvorlage für das Visual Studio-Paket  
 Die Projektvorlage für das Visual Studio-Paket finden Sie im Dialogfeld " **Neues Projekt** " im Ordner "C++ Extensibility".  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>So erstellen Sie ein VSPackage mithilfe der Visual Studio-Paket Vorlage  
  
1. Erstellen Sie ein Projekt mit der Visual Studio-Paket Vorlage.  
  
2. Wählen Sie die Option **benutzerdefinierter Editor** , und klicken Sie auf **weiter**. Die Seite **Editor-Optionen** wird angezeigt.  
  
3. Geben Sie den Namen des Editors in das Feld **Editor Name** ein. Geben Sie im Feld **Dateierweiterung** die Dateierweiterung ein, die dem Editor zugeordnet werden soll. Der Editor ist für Dateien mit dieser Erweiterung verfügbar. Die Dateierweiterung ist nur für Visual Studio registriert, nicht für Windows. Geben Sie im Feld **Standard Dateiname** den Standard Dateinamen für neue Dokumente ein, die mit Ihrem Editor erstellt wurden.  
  
4. Klicken Sie auf **Fertig stellen** , um Ihr VSPackage in dem von Ihnen angegebenen Ordner zu erstellen.  
  
### <a name="to-test-your-custom-editor"></a>So testen Sie den benutzerdefinierten Editor  
  
1. Zeigen Sie im Menü **Datei** auf **neu** , und klicken Sie dann auf **Datei**.  
  
2. Wählen Sie im Bereich **installierte Vorlagen** des Dialog Felds **neue Datei** die Datei Vorlage aus, und geben Sie dann den Dateityp an, den Sie gerade registriert haben.  
  
3. Klicken Sie auf **Öffnen** , um das Dokument anzuzeigen und zu bearbeiten.  
  
     Der Editor unterstützt Ausschneide-und Einfügevorgänge, Find-and-Replace-und Open-and-Load-Vorgänge.  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSPackages](../extensibility/internals/vspackages.md)
