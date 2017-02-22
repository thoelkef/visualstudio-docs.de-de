---
title: "Dateieigenschaften, JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "javascript.project.property.expandedsdknode.fileversion"
  - "javascript.project.property.expandedsdknode.uri"
  - "javascript.project.property.expandedsdknode.filename"
  - "javascript.project.property.reference.description"
  - "javascript.project.property.reference.specificversion"
  - "javascript.project.property.reference.identity"
  - "javascript.project.property.fullpath"
  - "javascript.project.property.packageaction"
  - "javascript.project.property.reference.package"
  - "javascript.project.property.copytooutputdirectory"
  - "javascript.project.property.expandedsdknode.sdkpath"
  - "javascript.project.property.reference.filetype"
  - "javascript.project.property.reference.culture"
  - "javascript.project.property.filename"
  - "javascript.project.property.reference.resolvedpath"
  - "javascript.project.property.reference.version"
ms.assetid: 085913b8-a97b-45f7-85fa-bbb0902f3ee9
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Dateieigenschaften, JavaScript
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Mit den Dateieigenschaften können Sie anzeigen, welche Aktionen das Projektsystem an den Dateien ausführen soll.  Beispielsweise können Sie Eigenschaften festlegen, um anzugeben, ob eine Datei zum Paket als Ressourcendatei hinzugefügt werden soll.  
  
 Sie können im Projektmappen\-Explorer eine beliebige Datei auswählen und dann ihre Eigenschaften im **Eigenschaftenfenster** untersuchen.  JavaScript\-Dateien haben vier Eigenschaften: **In Ausgabeverzeichnis kopieren**, **Paketaktion**, **Dateiname** und **Dateipfad**.  
  
## Dateieigenschaften  
 In diesem Abschnitt werden die Eigenschaften, die für JavaScript\-Dateien gemeinsam sind.  
  
### Eigenschaft In Ausgabeverzeichnis kopieren  
 Diese Eigenschaft bestimmt die Bedingungen, unter denen die ausgewählte Quelldatei in das Ausgabeverzeichnis kopiert wird.  Wählen Sie **Nicht kopieren** aus, wenn die Datei nie ins Ausgabeverzeichnis kopiert werden soll.  Wählen Sie **Immer kopieren** aus, wenn die Datei immer ins Ausgabeverzeichnis kopiert werden soll.  Wählen Sie **Kopieren, wenn neuer**, wenn die Datei nur kopiert werden soll, wenn sie neuer als eine vorhandene Datei mit demselben Namen im Ausgabeverzeichnis ist.  
  
### Paket\-Aktion  
 Die Eigenschaft **Paketaktion** gibt an, wie Visual Studio mit einer Datei ausgeführt werden, wenn ein Build ausgeführt wird.  **Paketaktion** kann einen der folgenden Werte aufweisen:  
  
-   **Keine** \- die Datei wird nicht im Paketmanifest enthalten.  Ein Beispiel ist eine Textdatei mit einer Dokumentation, z. B. eine Readme\-Datei.  
  
-   **Inhalt** \- Die Datei wird im Paketmanifest enthalten.  Beispielsweise ist diese Einstellung der Standardwert für .htm, ein JS\-Dateien, ein .css, ein Bild, eine Audio\- oder Videodatei.  
  
-   **Manifest** \- die Datei wird nicht im Paketmanifest enthalten.  Stattdessen wird die Datei für die Eingabe verwendet, wenn Sie das Paketmanifest generiert.  Dies ist der Standardwert für die package.appxmanifest\-Datei.  
  
-   **Ressource** \- die Datei wird nicht im Paketmanifest enthalten.  Stattdessen wird der Inhalt der Datei im Paket\-Ressourcen\-Index \(PRI\) indiziert der in das Paketmanifest wechselt.  Dies wird normalerweise für Ressourcendateien verwendet.  
  
 Der Standardwert für **Paketaktion** hängt von der Erweiterung der Datei ab, die Sie der Projektmappe hinzufügen.  
  
### FileName\-Eigenschaft  
 Zeigt den Dateinamen als schreibgeschützter \- Wert.  Um die Datei umbenennen, müssen Sie auf im Projektmappen\-Explorer mit der rechten Maustaste klicken und **Umbenennen** auswählen.  
  
### Eigenschaft des vollständigen Pfads  
 Zeigt den vollständigen Pfad zur Datei als schreibgeschützter \- Wert.  Um den Pfad der Datei ändern, können Sie Drag & Drop der Datei im Projektmappen\-Explorer.  
  
## Handakte\-Eigenschaften  
 In diesem Abschnitt werden die Eigenschaften, die auf Dateien gemeinsam sind, die von [!INCLUDE[win8_app_js](../../ide/reference/includes/win8_app_js_md.md)] verwiesen werden.  Wenn Sie einen Verweis wie eine .winmd\-Datei, einen SDK\-Verweis, einen Interprojektverweis oder einen Assemblyverweis im Projektmappen\-Explorer auswählen, werden möglicherweise andere Eigenschaften im Eigenschaftenfenster, entsprechend dem Dateityp an.  
  
### Kultur  
 Zeigt die Sprache an, die mit dem Verweis zugeordnet ist.  
  
### Dateityp  
 Zeigt den Dateityp des Verweises an.  
  
### Dateiversion  
 Zeigt die Dateiversion des Verweises an.  
  
### Identity  
 Zeigt die Identität des Verweises an, der im Projekt verwendet wird, das in der Projektdatei gespeichert wird.  
  
### Package  
 Zeigt den Namen des Paketmanifests an, das mit dem Verweis zugeordnet ist.  
  
### Aufgelöster Pfad  
 Zeigt den Pfad zum Verweis an, der im Projekt verwendet wird.  
  
### SDK Pfad  
 Zeigt den Pfad zur verwiesen wird SDK\-Datei an.  
  
### Uri  
 Zeigt den URI zu, der in HTML\- oder JavaScript\-Dateien des Projekts enthalten sein muss, um die Datei als Quelldatei einzuschließen.  
  
### Version  
 Zeigt die Version des Verweises an.  
  
## Siehe auch  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/de-de/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)