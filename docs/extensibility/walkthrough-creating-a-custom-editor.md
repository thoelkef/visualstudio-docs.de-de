---
title: "Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Erstellen von benutzerdefinierten - Editoren [Visual Studio SDK]"
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackage\-Projektvorlage kann einen einfachen benutzerdefinierten Editor in C\+\+ erstellen.  VSPackage\-Projektvorlage wird C\#\- oder Visual Basic\-Projekte nicht mehr unterstützt. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Vorbereitungsmaßnahmen  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Die Projektvorlage für Visual Studio\-Paket  
 Die Projektvorlage Visual Studio\-Paket finden Sie in der **Neues Projekt** Dialogfeld im Ordner C\+\+\-Erweiterbarkeit  
  
### Ein VSPackage mit der Visual Studio\-Paket\-Vorlage erstellen  
  
1.  Erstellen Sie ein Projekt mit der Vorlage für Visual Studio\-Paket.  
  
2.  Wählen Sie die **Editor für benutzerdefinierte** aus, und klicken Sie auf **Weiter**. Die **\-Editor\-Optionen** angezeigt wird.  
  
3.  Geben Sie den Namen des Editors in die **Name des Editors** Feld. Geben Sie die Erweiterung, die den Editor in zugeordnet werden soll die **Erweiterung** Feld. Der Editor ist für Dateien mit dieser Erweiterung verfügbar. Die Erweiterung ist nur für Visual Studio für Windows nicht registriert. Geben Sie den Standardnamen für neue Dokumente mit den Editor in die **Standarddateiname** Feld.  
  
4.  Klicken Sie auf **Fertig stellen**, um Ihr VSPackage in dem von Ihnen angegebenen Ordner zu erstellen.  
  
### Testen des benutzerdefinierten Editors  
  
1.  Auf der **Datei** auf **Neu** und klicken Sie dann auf **Datei**.  
  
2.  In der **Installierte Vorlagen** im Bereich der **neue Datei** wählen Sie im Dialogfeld die Vorlage, und klicken Sie dann auf die Datei Sie gerade registriert geben.  
  
3.  Klicken Sie auf **Öffnen** anzeigen und Bearbeiten des Dokuments.  
  
     Der Editor unterstützt Ausschneiden und einfügen, suchen und ersetzen und Open\-and\-Load\-Vorgänge.  
  
## Siehe auch  
 [VSPackages](../extensibility/internals/vspackages.md)