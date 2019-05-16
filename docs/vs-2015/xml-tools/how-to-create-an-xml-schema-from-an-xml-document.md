---
title: 'Vorgehensweise: Erstellen Sie ein XML-Schema aus einem XML-Dokument | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a732f0c6a9758de3ebd918559203b13a56d6a0ae
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697790"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Vorgehensweise: Erstellen eines XML-Schemas aus einem XML-Dokument
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der XML-Editor ermöglicht Ihnen, ein XSD-Schema (XML Schema Definition Language) aus einem XML-Dokument zu erstellen. Das XML-Instanzdokument bestimmt wie folgt, auf welche Weise das Schema generiert wird:  
  
- Wenn dem XML-Dokument kein Schema oder keine DTD (Document Type Definition) zugeordnet ist, wird mithilfe der Daten im XML-Dokument ein neues XML-Schema abgeleitet.  
  
- Wenn das XML-Dokument eine zugeordnete DTD enthält, werden die externe DTD und die interne Teilmenge in ein entsprechendes XML-Schema konvertiert.  
  
- Wenn das XML-Dokument ein XDR-Inlineschema (XML-Data Reduced) enthält, wird das XDR-Schema in ein entsprechendes XML-Schema konvertiert.  
  
  Mit den erstellten Schemata wird anschließend IntelliSense für das XML-Dokument bereitgestellt.  
  
  Weitere Informationen zum schemarückschlussmodul finden Sie unter [Herleiten eines XML-Schemas](https://msdn.microsoft.com/library/b18e7ffd-3c04-482d-9934-ba2f6a59b2c9).  
  
### <a name="to-create-an-xml-schema"></a>So erstellen Sie ein XML-Schema  
  
1. Laden Sie ein XML-Instanzdokument im XML-Editor.  
  
2. Klicken Sie auf die **Create Schema** Schaltfläche der **Symbolleiste**.  
  
     Ein XML-Schemadokument wird für jeden im XML-Instanzdokument gefundenen Namespace erstellt und geöffnet. Jedes Schema wird als sonstige temporäre Datei geöffnet.  
  
     Die Schemata können auf Datenträger gespeichert, dem Projekt hinzugefügt oder verworfen werden.  
  
    > [!NOTE]
    > Die **Create Schema** Befehl ist auch verfügbar im Kontextmenü des XML-Editor und wählen Sie unter den **XML** Menü.  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Editor](../xml-tools/xml-editor.md)
