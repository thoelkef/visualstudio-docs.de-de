---
title: "CreateExpInstance-Dienstprogramm | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "experimentelle builds"
  - "experimentellen Struktur"
  - "experimentelle Instanz"
  - "createexpinstance"
  - "createexpinst"
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# CreateExpInstance-Dienstprogramm
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Das Dienstprogramm CreateExpInstance um zu erstellen, zurücksetzen oder Löschen einer experimentellen Instanz von Visual Studio. Sie können die experimentelle Instanz, Debuggen und Testen von Visual Studio\-Erweiterungen ohne Änderung der zugrunde liegenden Produkt verwenden.  
  
## Syntax  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### Parameter  
 \/ Erstellen  
 Die experimentelle Instanz erstellt.  
  
 \/ Reset  
 Löscht die experimentelle Instanz und dann ein neues Zertifikat erstellt.  
  
 \/Clean  
 Löscht die experimentelle Instanz.  
  
 \/ VSInstance  
 Der Name des Verzeichnisses, das die zu kopierende Basis Visual Studio\-Instanz enthält.  
  
 \/ RootSuffix  
 Das Suffix an den Namen des Verzeichnisses experimentelle Instanz angefügt werden soll.  
  
## Hinweise  
 Wenn Sie Visual Studio\-Erweiterung arbeiten, können Sie durch Drücken auf F5, um die standardmäßige experimentelle Instanz öffnen und installieren Sie die aktuelle Erweiterung. Wenn keine experimentelle Instanz verfügbar ist, erstellt Visual Studio mit einem Konto mit den Standardeinstellungen.  
  
 Der Standardspeicherort der experimentellen Instanz hängt von der Visual Studio\-Versionsnummer ab. Beispielsweise ist der Speicherort für Visual Studio 2015 %localappdata%\\Microsoft\\VisualStudio\\14.0Exp\\ alle Dateien im Verzeichnis als Teil dieser Instanz. Alle zusätzlichen experimentellen Instanzen werden nicht von Visual Studio geladen werden, es sei denn, der Name des Verzeichnisses auf den standardmäßigen Speicherort geändert wird.  
  
 Visual Studio greift die Registrierung nicht, wenn sie die experimentelle Instanz geöffnet wird. Dies unterscheidet sich von früheren Versionen von Visual Studio, die eine Testversion der Registrierungsstruktur verwendet.  
  
 Das Dienstprogramm CreateExpInstance ersetzt das VsRegEx\-Dienstprogramm.  
  
 Das folgende Beispiel setzt die standardmäßige experimentelle Instanz von Visual Studio.  
  
 **CreateExpInstance.exe\/Reset \/VSInstance \= 14.0\/rootsuffix Exp \=**  
  
## Siehe auch  
 [Freigeben eines Produkts](../../misc/releasing-a-visual-studio-integration-product.md)