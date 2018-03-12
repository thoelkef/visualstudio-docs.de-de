---
title: 'Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9e8ea75cb96b36f885a55cbf9f174394379dc05a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-custom-editor"></a>Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors
Die VSPackage-Projektvorlage kann einen einfachen benutzerdefinierten Editor in C++ erstellen.  Die VSPackage-Projektvorlage wird C#- oder Visual Basic-Projekten nicht mehr unterstützt. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>Die Visual Studio-Paket-Projektvorlage  
 Die Visual Studio-Paket-Projektvorlage finden Sie in der **neues Projekt** Dialogfeld im Ordner "C++-Erweiterbarkeit"  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>So erstellen eine VSPackage mit der Visual Studio-Paket-Vorlage  
  
1.  Erstellen Sie ein Projekt mit Visual Studio-Paketvorlage ein.  
  
2.  Wählen Sie die **benutzerdefinierten Editors** aus, und klicken Sie auf **Weiter**. Die **Editoroptionen** angezeigt wird.  
  
3.  Geben Sie den Namen des Editors in die **editorname** Feld. Geben Sie die Dateierweiterung, die im Editor zugeordnet werden sollen die **Dateierweiterung** Feld. Der Editor ist für Dateien mit dieser Erweiterung verfügbar. Die Erweiterung wird nicht für Windows nur für Visual Studio registriert. Geben Sie für neue Dokumente mit Ihrem-Editor in der Standarddateiname der **Standarddateiname** Feld.  
  
4.  Klicken Sie auf **Fertig stellen** , um Ihr VSPackage in dem von Ihnen angegebenen Ordner zu erstellen.  
  
### <a name="to-test-your-custom-editor"></a>So testen Sie Ihre benutzerdefinierten editor  
  
1.  Auf der **Datei** Sie im Menü **neu** , und klicken Sie dann auf **Datei**.  
  
2.  In der **installierte Vorlagen** im Bereich der **neue Datei** wählen Sie im Dialogfeld der Vorlage, und klicken Sie dann auf die Datei, Sie die gerade registriert haben geben.  
  
3.  Klicken Sie auf **öffnen** anzeigen und bearbeiten das Dokument.  
  
     Der Editor unterstützt Ausschneiden und einfügen, suchen und ersetzen und Open-Load-Vorgänge.  
  
## <a name="see-also"></a>Siehe auch  
 [VSPackages](../extensibility/internals/vspackages.md)