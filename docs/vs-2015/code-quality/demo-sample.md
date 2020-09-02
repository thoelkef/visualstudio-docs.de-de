---
title: Demo Beispiel | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 3a49859a8cd1c4ffb01f93bf2539fc16c42f8c4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277887"
---
# <a name="demo-sample"></a>Demobeispiel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In den folgenden Verfahren wird gezeigt, wie Sie das Beispiel für Exemplarische Vorgehensweise [: Analysieren von C/C++-Code auf Fehler](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md)erstellen. Mithilfe dieser Prozeduren wird Folgendes erstellt:  
  
- Eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Lösung mit dem Namen "CppDemo".  
  
- Ein statisches Bibliotheksprojekt namens „CodeDefects“  
  
- Ein statisches Bibliotheksprojekt namens „Annotations“  
  
  Die Prozeduren stellen zudem den Code für den Header und die .cpp-Dateien für die statischen Bibliotheken bereit.  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Erstellen der CppDemo-Projektmappe und des CodeDefects-Projekts  
  
1. Klicken Sie auf das Menü **Datei**, zeigen Sie auf die Option **Neu**, und klicken Sie anschließend auf **Neues Projekt**.  
  
2. Wenn Visual C++ nicht Ihre Standardsprache in VS ist, erweitern Sie in der Baumstruktur **Projekttypen** die Option **Andere Sprachen**.  
  
3. Erweitern Sie **Visual C++**, und klicken Sie dann auf **Allgemein**.  
  
4. Klicken Sie unter **Vorlagen** auf **Leeres Projekt**.  
  
5. Geben Sie im Textfeld **Name****CodeDefects** ein.  
  
6. Aktivieren Sie das Kontrollkästchen **Verzeichnis für Projektmappe erstellen**.  
  
7. Geben Sie im Textfeld Projektmappenname den **Namen** **CppDemo**ein.  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>Konfigurieren des CodeDefects-Projekts als statische Bibliothek  
  
1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **CodeDefects**, und klicken Sie dann auf **Eigenschaften**.  
  
2. Erweitern Sie **Konfigurationseigenschaften**, und klicken Sie dann auf **Allgemein**.  
  
3. Wählen Sie in der Liste **Allgemein** den Text in der Spalte neben **Zielerweiterung** aus, und geben Sie dann **.lib** ein.  
  
4. Klicken Sie unter **Projektstandards** auf die Spalte neben **Konfigurationstyp** und dann auf **Statische Bibliothek (.lib)**.  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Hinzufügen der Kopf- und Quelldatei zum CodeDefects-Projekt  
  
1. Erweitern Sie im Projektmappen-Explorer **CodeDefects**, klicken Sie mit der rechten Maustaste auf **Headerdateien**, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**.  
  
2. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Code** und dann auf **Headerdatei (.h)**.  
  
3. Geben Sie im Feld **Name** die Bezeichnung **Bug.cpp** ein, und klicken Sie dann auf **Hinzufügen**.  
  
4. Kopieren Sie den folgenden Code, und fügen Sie ihn in die Datei " **Bug. cpp** " im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor ein.  
  
    ```  
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **Quelldateien**, zeigen Sie auf **Neu**, und klicken Sie anschließend auf **Neues Element**.  
  
6. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **C++-Datei (.cpp)**.  
  
7. Geben Sie im Feld **Name** die Bezeichnung **Bug.cpp** ein, und klicken Sie dann auf **Hinzufügen**.  
  
8. Kopieren Sie den folgenden Code, und fügen Sie ihn in die Datei "Bug. h" im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor ein.  
  
    ```  
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
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
        return i+j;   
    }  
    ```  
  
9. Klicken Sie auf das Menü **Datei** und dann auf **Alle speichern**.  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Hinzufügen des Annotations-Projekts und Konfigurieren dieses Projekts als statische Bibliothek  
  
1. Klicken Sie im Projektmappen-Explorer auf **CppDemo**, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Projekt**.  
  
2. Erweitern Sie im Dialogfeld **Neues Projekt hinzufügen** die Option „Visual C++“, klicken Sie auf **Allgemein**, und klicken Sie dann auf **Leeres Projekt**.  
  
3. Geben Sie im Textfeld **Name** den Namen **Annotations** ein, und klicken Sie dann auf **Hinzufügen**.  
  
4. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **Annotations**, und klicken Sie dann auf **Eigenschaften**.  
  
5. Erweitern Sie **Konfigurationseigenschaften**, und klicken Sie dann auf **Allgemein**.  
  
6. Wählen Sie in der Liste **Allgemein** den Text in der Spalte neben **Zielerweiterung** aus, und geben Sie dann **.lib** ein.  
  
7. Klicken Sie unter **Projektstandards** auf die Spalte neben **Konfigurationstyp** und dann auf **Statische Bibliothek (.lib)**.  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Hinzufügen der Headerdatei und Quelldatei zum Annotations-Projekt  
  
1. Erweitern Sie im Projektmappen-Explorer **Annotations**, klicken Sie mit der rechten Maustaste auf **Headerdateien**, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**.  
  
2. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Headerdatei (.h)**.  
  
3. Geben Sie im Feld **Name** den **annotations.h** ein, und klicken Sie dann auf **Hinzufügen**.  
  
4. Kopieren Sie den folgenden Code, und fügen Sie ihn in die Datei " **Annotations. h** " im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor ein.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **Quelldateien**, zeigen Sie auf **Neu**, und klicken Sie anschließend auf **Neues Element**.  
  
6. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Code** und dann auf **C++-Datei (.cpp)**.  
  
7. Geben Sie im Feld **Name** den **annotations.cpp** ein, und klicken Sie dann auf **Hinzufügen**.  
  
8. Kopieren Sie den folgenden Code, und fügen Sie ihn in die Datei " **Annotations. cpp** " im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor ein.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. Klicken Sie auf das Menü **Datei** und dann auf **Alle speichern**.
