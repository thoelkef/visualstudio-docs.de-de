---
title: 'Vorgehensweise: Auswählen der zu verwendenden XML-Schemas | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93f573412524619292b1966e87abeda11cc0813a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863723"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Gewusst wie: Auswählen der zu verwendenden XML-Schemas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Der XML-Editor stellt einen Schemacache im Verzeichnis "%InstallDir%\Xml\Schemas" bereit. Der Schemacache enthält bekannte XML-Schemata, die für IntelliSense und zur Validierung von XML-Dokumenten verwendet werden.  
  
 Die **Schemas** Document-Eigenschaft wird verwendet, um Wählen Sie eine oder mehrere XML-Schema Definition Language (XSD) Schemas verwenden. Sie können damit Schemas aus dem Schemacache auswählen oder ein Schema angeben, das sich nicht im Cache befindet.  
  
 Die von Ihnen ausgewählten Schemas werden zusammen mit den anderen XML-Dokumenteigenschaften in der versteckten Projektmappen-Benutzeroptionendatei (.suo) abgespeichert. Daher müssen Sie diese Werte nicht erneut eingeben, wenn Sie die Projektmappe das nächste Mal öffnen.  
  
> [!NOTE]
>  Der Editor kann mithilfe eines Inlineschemas oder eines Schemas, auf das von dem `xsd:schemaLocation`-Attribut verwiesen wird, die Validierung vornehmen. Weitere Informationen finden Sie unter [XML-Dokumentvalidierung](../xml-tools/xml-document-validation.md).  
  
### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>So wählen Sie ein XML-Schema aus dem Schemacache aus  
  
1. Öffnen Sie eine Datei im XML-Editor.  
  
2. Klicken Sie im Eigenschaftenfenster Dokuments, auf die Schaltfläche auf der **Schemas** Feld.  
  
    Die **XML-Schemas** Dialogfeld wird angezeigt. Das Dialogfeld listet alle Schemata mit einer XSD-Erweiterung im Schemacache (z. B. Schemas, die in der Datei catalog.xml verwiesen wird), und auch jedes Schema, das in der aktuellen Projektmappe öffnen, in Visual Studio verwiesen wird, eine `xsd:schemaLocation` Attribut, oder auf die verwiesen wird. die **Schemas** Eigenschaft.  
  
3. Wählen Sie Schemata zu Validierungszwecken aus, indem Sie eine der folgenden Methoden verwenden:  
  
   - Wählen Sie ein Schema aufgeführt, die der **XML-Schemas** Dialogfeld klicken Sie auf die **verwenden** Spalte, und wählen Sie dann **dieses Schema verwenden**.  
  
     - oder -   
  
   - Wählen Sie mehrere Schemas aufgeführt, die der **XML-Schemas** Dialogfeld, mit der rechten Maustaste, und wählen **dieses Schema verwenden**.  
  
4. Klicken Sie auf **OK**.  
  
    Die Liste der ausgewählten Schemas wird kopiert, an die **Schemas** -Dokumenteigenschaft.  
  
### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>So fügen Sie dem Schemacache ein XML-Schema hinzu  
  
1.  Klicken Sie im Eigenschaftenfenster Dokuments, auf die Schaltfläche auf der **Schemas** Feld.  
  
2.  Klicken Sie auf **Hinzufügen**.  
  
     Daraufhin wird die **XSD-Schema öffnen** Dialogfeld.  
  
3.  Navigieren Sie zu den Schemas, die dem Schemacache hinzugefügt werden sollen, und markieren Sie diese.  
  
4.  Klicken Sie auf **öffnen**.  
  
     Die Schemas, die dem Schema hinzugefügt und die **verwenden** Spaltenwert wird festgelegt, um **dieses Schema verwenden**.  
  
### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>So löschen Sie ein XML-Schema aus dem Schemacache  
  
1.  Klicken Sie im Eigenschaftenfenster Dokuments, auf die Schaltfläche auf der **Schemas** Feld.  
  
2.  Wählen Sie das Schema zu entfernen, und klicken Sie dann auf **entfernen**.  
  
     Das Schema wird aus dem In-Memory-Schemacache , jedoch nicht aus dem Dateisystem entfernt.  
  
    > [!NOTE]
    >  Wenn Sie einen Verweis auf das Schema über noch einen `schemaLocation` Attribut oder ein entsprechendes `targetNamespace` klicken Sie dann **entfernen** funktioniert nicht in dieser Situation aufgrund der automatischen Zuordnung. In diesem Fall wird empfohlen, Sie das Schema als markieren **ausgewählte Schemas nicht verwenden** in die **verwenden** Spalte.  
  
## <a name="see-also"></a>Siehe auch  
 [Schemacache](../xml-tools/schema-cache.md)   
 [XML-Schemata (Dialogfeld)](../xml-tools/xml-schemas-dialog-box.md)   
 [XML-Editor](../xml-tools/xml-editor.md)



