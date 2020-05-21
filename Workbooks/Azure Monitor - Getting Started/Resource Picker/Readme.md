# <a name="picking-a-set-of-resources-to-analyze-in-workbooks"></a>Wybieranie zestawu zasobów do analizowania w skoroszytach

Szablon `Resource Picker` ułatwia rozpoczęcie pracy z parametrami subskrypcji, grupy zasobów i zasobów w celu skonfigurowania kontekstu wejściowego skoroszytu. Domyślne parametry są ustawione do wybierania maszyn wirtualnych, ale można je skonfigurować do wybierania dowolnego typu zasobu. Szablon zawiera również kontrolkę zapytania argumentu, która pokazuje, jak używać parametrów w analizach.

![Image (Obraz)](Full.png)

## <a name="setting-up-the-resource-type-to-pick"></a>Konfigurowanie typu zasobu do wybrania

1. Wybierz pozycję `Edit` (Edytuj) na pasku narzędzi skoroszytu.
2. Teraz powinna być widoczna lista rozwijana `Resource type` przed elementem `Subscriptions`:

    ![Image (Obraz)](Parameter.png)
3. Rozwiń listę rozwijaną i wybierz typy zasobów, które mają być wybierane. Spowoduje to zaktualizowanie subskrypcji, grupy zasobów i listy rozwijanej zasobów w celu dopasowania do dokonanego wyboru.
4. Kliknij przycisk `Edit` w prawym dolnym rogu kontrolki parametrów.
5. W siatce parametrów dla wiersza `Resources` zmień kolumnę `Display name` z _Maszyny wirtualne_ na przyjazną nazwę wybranego typu zasobu (np. _Konta magazynu_)
6. Kliknij pozycję `Done Editing` na pasku narzędzi skoroszytów.

## <a name="selecting-more-or-less-than-10-resources-by-default"></a>Domyślne wybieranie więcej lub mniej niż 10 zasobów

1. Wybierz pozycję `Edit` (Edytuj) na pasku narzędzi skoroszytu.
2. Kliknij przycisk `Edit` w prawym dolnym rogu kontrolki parametrów.
3. W siatce parametrów wybierz wiersz `Resources`
4. Kliknij pasek narzędzi kontrolki ikony `Edit` (lub ołówka).
5. W okienku `Edit Parameter`, które zostanie wyświetlone, przewiń w dół do edytora `Azure Resource Graph Query`. Powinien on zawierać zapytanie, które wygląda następująco:
    ```sql
    Resources
    | where type in~({ResourceTypes})
    | extend resourceGroupId = strcat('/subscriptions/', subscriptionId, '/resourceGroups/', resourceGroup)
    | where resourceGroupId in~({ResourceGroups}) or '*' in~({ResourceGroups})
    | order by name asc
    | extend Rank = row_number()
    | project value = id, label = name, selected = Rank <= 10, group = resourceGroup
    ```
    Kod wybierania zasobów znajduje się w ostatnim wierszu zapytania: `selected = Rank <= 10`. 

6. Zmień wartość z 10 na inną, aby zmienić domyślny wybór