# Elec2
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity3">

    <ListView
        android:id="@+id/listView"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_above="@+id/deleteButton"
        android:layout_marginTop="10dp"
        android:choiceMode="multipleChoice" />

    <Button
        android:id="@+id/addButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_alignParentEnd="true"

        android:text="Add" />

    <Button
        android:id="@+id/deleteButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_toStartOf="@+id/addButton"
        android:layout_marginEnd="8dp"
        android:text="Remove Selected" />

    <EditText
        android:id="@+id/editText"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_above="@id/deleteButton"
        android:hint="Enter a task" />

</RelativeLayout>


-----------------------------------------------------------------------------------------------------------------------------
deleteButton.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View v) {
                    SparseBooleanArray checkedItemPositions = listView.getCheckedItemPositions();
                    if (checkedItemPositions != null && checkedItemPositions.size() > 0) {
                        for (int i = adapter.getCount() - 1; i >= 0; i--) {
                            if (checkedItemPositions.get(i)) {
                                adapter.remove(adapter.getItem(i));
                            }
                        }
                        listView.clearChoices();
                        adapter.notifyDataSetChanged();
                    } else {
                        Toast.makeText(getApplicationContext(), "Please select at least one task to delete.", Toast.LENGTH_SHORT).show();
                    }
                }
            });
            
            
