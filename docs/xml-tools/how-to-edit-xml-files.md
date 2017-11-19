---
title: 'Vorgehensweise: Bearbeiten von XML-Dateien | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cda89cc132ecd496605c19194c0221de503f4469
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-edit-xml-files"></a>Gewusst wie: Bearbeiten von XML-Dateien
Der XML-Editor ist der neue Editor für XML-Dateien. Er kann für eine eigenständige XML-Datei oder für eine einem Visual Studio-Projekt zugeordnete Datei verwendet werden. Der XML-Editor ist den folgenden Dateierweiterungen zugeordnet: .config, .dtd, .xml, .xsd, .xdr, .xsl, .xslt und .vssettings. Dem XML-Editor wird auch jeder andere Dateityp mit XML- bzw. DTD-Inhalten zugeordnet, für den kein bestimmter Editor registriert ist.  
  
> [!NOTE]
>  XHTML-Dokumente werden vom HTML-Editor behandelt.  
  
### <a name="to-edit-an-xml-file"></a>So bearbeiten Sie eine XML-Datei  
  
1.  Doppelklicken Sie auf die Datei, die Sie bearbeiten möchten.  
  
### <a name="to-add-a-new-xml-file-to-a-project"></a>So fügen Sie einem Projekt eine neue XML-Datei hinzu  
  
1.  Aus der **Projekt** klicken Sie im Menü **neues Element hinzufügen**.  
  
2.  Wählen Sie **XML-Datei** aus der **Vorlagen** Bereich.  
  
3.  Geben Sie den Dateinamen in der **Namen** Feld, und drücken Sie **hinzufügen**.  
  
     Die XML-Datei wird dem Projekt hinzugefügt und im XML-Editor geöffnet. Die Datei enthält die XML-Standarddeklaration, `<?xml version="1.0" encoding="utf-8" ?>`.  
  
### <a name="to-add-an-existing-xml-file-to-a-project"></a>So fügen Sie einem Projekt eine vorhandene XML-Datei hinzu  
  
1.  Aus der **Projekt** klicken Sie im Menü **vorhandenes Element hinzufügen**.  
  
     Die **vorhandenes Element hinzufügen** Dialogfeld wird angezeigt.  
  
2.  Wählen Sie eine XML-Datei, und drücken Sie **hinzufügen**.  
  
### <a name="to-create-a-new-xml-or-xslt-file"></a>So erstellen Sie eine neue XML- oder XSLT-Datei  
  
1.  Aus der **Datei** klicken Sie im Menü **neu**.  
  
     Die **neue Datei** Dialogfeld wird angezeigt.  
  
2.  Wählen Sie **XML-Datei** zum Erstellen einer neuen XML-Datei, oder wählen Sie **XSLT-Datei** um ein neues XSLT-Stylesheet zu erstellen.  
  
3.  Klicken Sie auf **öffnen**.  
  
### <a name="to-create-a-project-for-xml-files"></a>So erstellen Sie ein Projekt für XML-Dateien  
  
1.  Aus der **Datei** klicken Sie im Menü **neu**, und wählen Sie dann **Projekt**.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  Wählen Sie die Codesprache Ihrer Wahl, select **leeres Projekt**, und klicken Sie auf **OK**.  
  
3.  Fügen Sie dem Projekt XML-Dateien hinzu.  
  
     Der XML-Editor sucht die dem Projekt hinzugefügten Schemata und verwendet sie für die Validierung und für IntelliSense in allen XML-, Schema- oder XSLT-Dateien, die Sie bearbeiten, während das Projekt geöffnet ist.  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Editor](../xml-tools/xml-editor.md)   
 [XML-Dokumenteigenschaften, Eigenschaftenfenster](../xml-tools/xml-document-properties-properties-window.md)   
 [Gewusst wie: Erstellen eines XML-Schemas aus einem XML-Dokument](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)