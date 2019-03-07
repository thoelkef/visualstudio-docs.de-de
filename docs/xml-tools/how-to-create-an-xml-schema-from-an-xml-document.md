---
title: Erstellen eines XML-Schemas
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e93155f230ee4a564116f5d1357a97923706c36
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526128"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Vorgehensweise: Erstellen Sie ein XML-Schema aus einem XML-Dokument

Der XML-Editor können Sie ein Schema für XML Schema Definition Language (XSD) aus einem XML-Dokument zu erstellen. Die XML-Datei wird bestimmt, wie das Schema generiert wird, auf folgende Weise:

- Wenn dem XML-Dokument kein Schema oder keine DTD (Document Type Definition) zugeordnet ist, wird mithilfe der Daten im XML-Dokument ein neues XML-Schema abgeleitet.

- Wenn das XML-Dokument eine zugeordnete DTD enthält, werden die externe DTD und die interne Teilmenge in ein entsprechendes XML-Schema konvertiert.

- Wenn das XML-Dokument ein XDR-Inlineschema (XML-Data Reduced) enthält, wird das XDR-Schema in ein entsprechendes XML-Schema konvertiert.

Klicken Sie dann werden die Schemas, die erstellt werden verwendet, IntelliSense für die XML-Datei bereitgestellt.

Weitere Informationen zum schemarückschlussmodul finden Sie unter [Herleiten ein XML-Schemas](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>So erstellen Sie ein XML-Schema

1. Öffnen Sie eine XML-Datei in Visual Studio.

2. Wählen Sie auf der Menüleiste **XML** > **Create Schema**.

   Ein XML-Schema-Dokument erstellt und für jeden Namespace finden Sie in der XML-Datei geöffnet. Jedes Schema wird als sonstige temporäre Datei geöffnet. Die Schemata können auf Datenträger gespeichert, dem Projekt hinzugefügt oder verworfen werden.

## <a name="see-also"></a>Siehe auch

- [XML-editor](../xml-tools/xml-editor.md)