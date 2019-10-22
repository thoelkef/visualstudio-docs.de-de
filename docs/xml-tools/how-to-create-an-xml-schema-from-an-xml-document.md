---
title: Erstellen eines XML-Schemas
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 73563d732aab48192892794c15750bc9e5d3eb6a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645968"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Gewusst wie: Erstellen eines XML-Schemas aus einem XML-Dokument

Mit dem XML-Editor können Sie ein XSD-Schema (XML Schema Definition Language) aus einem XML-Dokument erstellen. Die XML-Datei bestimmt, wie das Schema auf folgende Weise generiert wird:

- Wenn dem XML-Dokument kein Schema oder keine DTD (Document Type Definition) zugeordnet ist, wird mithilfe der Daten im XML-Dokument ein neues XML-Schema abgeleitet.

- Wenn das XML-Dokument eine zugeordnete DTD enthält, werden die externe DTD und die interne Teilmenge in ein entsprechendes XML-Schema konvertiert.

- Wenn das XML-Dokument ein XDR-Inlineschema (XML-Data Reduced) enthält, wird das XDR-Schema in ein entsprechendes XML-Schema konvertiert.

Die Schemas, die erstellt werden, werden dann verwendet, um IntelliSense für die XML-Datei bereitzustellen.

Weitere Informationen zur Schema Rückschluss-Engine finden Sie unter ableiten [eines XML-Schemas](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>So erstellen Sie ein XML-Schema

1. Öffnen Sie eine XML-Datei in Visual Studio.

2. Wählen Sie in der Menüleiste die Option **XML** - > **Schema erstellen**aus.

   Ein XML-Schema Dokument wird für jeden in der XML-Datei gefundenen Namespace erstellt und geöffnet. Jedes Schema wird als sonstige temporäre Datei geöffnet. Die Schemata können auf Datenträger gespeichert, dem Projekt hinzugefügt oder verworfen werden.

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)