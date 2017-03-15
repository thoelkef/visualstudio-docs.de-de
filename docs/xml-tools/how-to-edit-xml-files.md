---
title: "Gewusst wie: Bearbeiten von XML-Dateien | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Gewusst wie: Bearbeiten von XML-Dateien
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der XML\-Editor ist der neue Editor für XML\-Dateien.Er kann für eine eigenständige XML\-Datei oder für eine einem Visual Studio\-Projekt zugeordnete Datei verwendet werden.Der XML\-Editor ist den folgenden Dateierweiterungen zugeordnet: .config, .dtd, .xml, .xsd, .xdr, .xsl, .xslt und .vssettings.Dem XML\-Editor wird auch jeder andere Dateityp mit XML\- bzw. DTD\-Inhalten zugeordnet, für den kein bestimmter Editor registriert ist.  
  
> [!NOTE]
>  XHTML\-Dokumente werden vom HTML\-Editor behandelt.  
  
### So bearbeiten Sie eine XML\-Datei  
  
1.  Doppelklicken Sie auf die Datei, die Sie bearbeiten möchten.  
  
### So fügen Sie einem Projekt eine neue XML\-Datei hinzu  
  
1.  Wählen Sie im Menü **Projekt** die Option **Neues Element hinzufügen** aus.  
  
2.  Wählen Sie im Bereich **Vorlagen** die Option **XML\-Datei** aus.  
  
3.  Geben Sie im Feld **Name** den Dateinamen ein, und klicken Sie auf **Hinzufügen**.  
  
     Die XML\-Datei wird dem Projekt hinzugefügt und im XML\-Editor geöffnet.Die Datei enthält die XML\-Standarddeklaration, `<?xml version="1.0" encoding="utf-8" ?>`.  
  
### So fügen Sie einem Projekt eine vorhandene XML\-Datei hinzu  
  
1.  Wählen Sie im Menü **Projekt** die Option **Vorhandenes Element hinzufügen** aus.  
  
     Das Dialogfeld **Vorhandenes Element hinzufügen** wird angezeigt.  
  
2.  Wählen Sie eine XML\-Datei aus, und klicken Sie auf **Hinzufügen**.  
  
### So erstellen Sie eine neue XML\- oder XSLT\-Datei  
  
1.  Wählen Sie im Menü **Datei** die Option **Neu** aus.  
  
     Das Dialogfeld **Neue Datei** wird angezeigt.  
  
2.  Wählen Sie **XML\-Datei** aus, um eine neue XML\-Datei zu erstellen, oder wählen Sie **XSLT\-Datei** aus, um ein neues XSLT\-Stylesheet zu erstellen.  
  
3.  Klicken Sie auf **Öffnen**.  
  
### So erstellen Sie ein Projekt für XML\-Dateien  
  
1.  Klicken Sie im Menü **Datei** auf **Neu**, und wählen Sie anschließend **Projekt** aus.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  Wählen Sie die gewünschte Codesprache aus, wählen Sie **Leeres Projekt** aus, und klicken Sie auf **OK**.  
  
3.  Fügen Sie dem Projekt XML\-Dateien hinzu.  
  
     Der XML\-Editor sucht die dem Projekt hinzugefügten Schemata und verwendet sie für die Validierung und für IntelliSense in allen XML\-, Schema\- oder XSLT\-Dateien, die Sie bearbeiten, während das Projekt geöffnet ist.  
  
## Siehe auch  
 [XML\-Editor](../xml-tools/xml-editor.md)   
 [XML\-Dokumenteigenschaften, Eigenschaftenfenster](../xml-tools/xml-document-properties-properties-window.md)   
 [Gewusst wie: Erstellen eines XML\-Schemas aus einem XML\-Dokument](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)