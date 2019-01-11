---
title: 'Vorgehensweise: Erstellen eines XML-Schemas aus einem XML-Dokument'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 629519a6df8c570ee806ec7360e03f442042b5ba
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915204"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Vorgehensweise: Erstellen Sie ein XML-Schema aus einem XML-Dokument

Der XML-Editor ermöglicht Ihnen, ein XSD-Schema (XML Schema Definition Language) aus einem XML-Dokument zu erstellen. Das XML-Instanzdokument bestimmt wie folgt, auf welche Weise das Schema generiert wird:

-   Wenn dem XML-Dokument kein Schema oder keine DTD (Document Type Definition) zugeordnet ist, wird mithilfe der Daten im XML-Dokument ein neues XML-Schema abgeleitet.

-   Wenn das XML-Dokument eine zugeordnete DTD enthält, werden die externe DTD und die interne Teilmenge in ein entsprechendes XML-Schema konvertiert.

-   Wenn das XML-Dokument ein XDR-Inlineschema (XML-Data Reduced) enthält, wird das XDR-Schema in ein entsprechendes XML-Schema konvertiert.

Mit den erstellten Schemata wird anschließend IntelliSense für das XML-Dokument bereitgestellt.

Weitere Informationen zum schemarückschlussmodul finden Sie unter [Herleiten eines XML-Schemas](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>So erstellen Sie ein XML-Schema

1.  Laden Sie ein XML-Instanzdokument im XML-Editor.

2.  Klicken Sie auf die **Create Schema** Schaltfläche der **Symbolleiste**.

     Ein XML-Schemadokument wird für jeden im XML-Instanzdokument gefundenen Namespace erstellt und geöffnet. Jedes Schema wird als sonstige temporäre Datei geöffnet.

     Die Schemata können auf Datenträger gespeichert, dem Projekt hinzugefügt oder verworfen werden.

    > [!NOTE]
    >  Die **Create Schema** Befehl ist auch verfügbar im Kontextmenü des XML-Editor und wählen Sie unter den **XML** Menü.

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)