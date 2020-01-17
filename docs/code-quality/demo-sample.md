---
title: C++-Beispielprojekt für die Codeanalyse
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 84f6ddc2012617a5216c58fa0761dc100fb8942f
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/25/2019
ms.locfileid: "75402742"
---
# <a name="sample-c-project-for-code-analysis"></a>C++-Beispielprojekt für die Codeanalyse

Diese folgenden Prozeduren zeigen Ihnen, wie Sie das Beispiel für [Exemplarische Vorgehensweise: Analysieren von C/C++-Code im Hinblick auf Fehler](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md) erstellen. Mithilfe dieser Prozeduren wird Folgendes erstellt:

- Eine [!INCLUDEvsprvs]-Projektmappe namens „CppDemo“

- Ein statisches Bibliotheksprojekt namens „CodeDefects“

- Ein statisches Bibliotheksprojekt namens „Annotations“

Die Prozeduren stellen zudem den Code für den Header und die *.cpp*-Dateien für die statischen Bibliotheken bereit.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Erstellen der CppDemo-Projektmappe und des CodeDefects-Projekts

1. Öffnen Sie [!INCLUDEvsprvs] und wählen Sie **Neues Projekt erstellen** aus.

2. Ändern Sie den Sprachfilter in **C++** .

3. Wählen Sie **Leeres Projekt** aus und klicken Sie auf **Weiter**.

4. Geben Sie im Textfeld **Projektname** **CodeDefects** ein.

5. Geben Sie im Textfeld **Projektmappenname** **CppDemo** ein.

6. Klicken Sie auf **Erstellen**

## <a name="configure-the-codedefects-project-as-a-static-library"></a>Konfigurieren des CodeDefects-Projekts als statische Bibliothek

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **CodeDefects**, und klicken Sie dann auf **Eigenschaften**.

2. Erweitern Sie **Konfigurationseigenschaften**, und klicken Sie dann auf **Allgemein**.

3. Ändern Sie in der Liste **Allgemein** die Option **Konfigurationstyp** in **Statische Bibliothek (.lib)** .

4. Ändern Sie in der Liste **Erweitert** die **Zieldateierweiterung** in **.lib**.

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Hinzufügen der Kopf- und Quelldatei zum CodeDefects-Projekt

1. Erweitern Sie im Projektmappen-Explorer **CodeDefects**, klicken Sie mit der rechten Maustaste auf **Headerdateien**, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**.

2. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Code** und dann auf **Headerdatei (.h)** .

3. Geben Sie im Feld **Name** die Bezeichnung **Bug.h** ein, und klicken Sie dann auf **Hinzufügen**.

4. Kopieren Sie den folgenden Code und fügen Sie ihn im Editor in der Datei *Bug.h* ein.

```cpp
#pragma once

#include <windows.h>

// These functions are consumed by the sample
// but are not defined. This project cannot be linked!
bool CheckDomain(LPCTSTR);
HRESULT ReadUserAccount();

// These constants define the common sizes of the
// user account information throughout the program
const int USER_ACCOUNT_LEN = 256;
const int ACCOUNT_DOMAIN_LEN = 128;
```

5. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **Quelldateien**, zeigen Sie auf **Neu**, und klicken Sie anschließend auf **Neues Element**.

6. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **C++-Datei (.cpp)** .

7. Geben Sie im Feld **Name** die Bezeichnung **Bug.cpp** ein, und klicken Sie dann auf **Hinzufügen**.

8. Kopieren Sie den folgenden Code und fügen Sie ihn im Editor in der Datei *Bug.cpp* ein.

```cpp
#include "Bug.h"

// the user account
TCHAR g_userAccount[USER_ACCOUNT_LEN] = {};
int len = 0;

bool ProcessDomain()
{
    TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];
    // ReadUserAccount gets a 'domain\user' input from
    //the user into the global 'g_userAccount'
    if (ReadUserAccount())
    {
        // Copies part of the string prior to the '\'
        // character onto the 'domain' buffer
        for (len = 0; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != L'\0'); len++)
        {
            if (g_userAccount[len] == '\\')
            {
                // Stops copying on the domain and user separator ('\')
                break;
            }
            domain[len] = g_userAccount[len];
        }
        if ((len = ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
        {
            // '\' was not found. Invalid domain\user string.
            delete[] domain;
            return false;
        }
        else
        {
            domain[len] = '\0';
        }
        // Process domain string
        bool result = CheckDomain(domain);

        delete[] domain;
        return result;
    }
    return false;
}

int path_dependent(int n)
{
    int i;
    int j;
    if (n == 0)
        i = 1;
    else
        j = 1;
    return i + j;
}
```

9. Klicken Sie auf das Menü **Datei** und dann auf **Alle speichern**.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Hinzufügen des Annotations-Projekts und Konfigurieren dieses Projekts als statische Bibliothek

1. Klicken Sie im Projektmappen-Explorer auf **CppDemo**, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Projekt**.

2. Ändern Sie im Dialogfeld **Neues Projekt hinzufügen** den Sprachfilter in **C++** , wählen Sie **Leeres Projekt** aus und klicken Sie auf **Weiter**.

3. Geben Sie im Textfeld **Projektname** den Namen **Annotations** ein, und klicken Sie dann auf **Erstellen**.

4. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **Annotations**, und klicken Sie dann auf **Eigenschaften**.

5. Erweitern Sie **Konfigurationseigenschaften**, und klicken Sie dann auf **Allgemein**.

6. Ändern Sie in der Liste **Allgemein** die Option **Konfigurationstyp** und klicken Sie dann auf **Statische Bibliothek (.lib)** .

7. Wählen Sie in der Liste **Erweitert** den Text in der Spalte neben **Zieldateierweiterung** aus, und geben Sie dann **.lib** ein.


## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Hinzufügen der Headerdatei und Quelldatei zum Annotations-Projekt

1. Erweitern Sie im Projektmappen-Explorer **Annotations**, klicken Sie mit der rechten Maustaste auf **Headerdateien**, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**.

2. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Headerdatei (.h)** .

3. Geben Sie im Feld **Name** den **annotations.h** ein, und klicken Sie dann auf **Hinzufügen**.

4. Kopieren Sie den folgenden Code, und fügen Sie ihn im Editor in der Datei *annotations.h* ein.

```cpp
#pragma once
#include <sal.h>

struct LinkedList
{
    struct LinkedList* next;
    int data;
};

typedef struct LinkedList LinkedList;

_Ret_maybenull_ LinkedList* AllocateNode();
```

5. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **Quelldateien**, zeigen Sie auf **Neu**, und klicken Sie anschließend auf **Neues Element**.

6. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Code** und dann auf **C++-Datei (.cpp)** .

7. Geben Sie im Feld **Name** den **annotations.cpp** ein, und klicken Sie dann auf **Hinzufügen**.

8. Kopieren Sie den folgenden Code, und fügen Sie ihn im Editor in der Datei *annotations.cpp* ein.

```cpp
#include "annotations.h"

LinkedList* AddTail(LinkedList* node, int value)
{
    // finds the last node
    while (node->next != nullptr)
    {
        node = node->next;
    }

    // appends the new node
    LinkedList* newNode = AllocateNode();
    newNode->data = value;
    newNode->next = 0;
    node->next = newNode;

    return newNode;
}
```

9. Klicken Sie auf das Menü **Datei** und dann auf **Alle speichern**.


Die Projektmappe ist jetzt fertig und sollte ohne Fehler erstellt werden.
