Implementation:

1) Add the element to your layout.xml file

<com.yourname.yourpackage.CleanEditText
	android:layout_width="wrap_content"
	android:layout_height="wrap_content"
	android:id="@+id/cleanEditText"/>

2) In your onCreate method, declare and initialize CleanEditText (ex: CleanEditText myNameInput)

CleanEditText myNameInput = (CleanEditText) findViewById(R.id.cleanEditText);

3) Implement the onImeBack action and onTouchListener for the CleanEditText

myNameInput.setOnTouchListener(new View.OnTouchListener() {
        @Override
        public boolean onTouch(View v, MotionEvent event) {
            v.onTouchEvent(event);
            myNameInput.setCursorVisible(true);
            return true;
        }
    });

myNameInput.setOnEditTextImeBackListener(new CleanEditText.EditTextImeBackListener() {
	    @Override
	    public void onImeBack(CleanEditText ctrl, String text) {
		myNameInput.setCursorVisible(false);
		myNameInput.clearComposingText(); // fixes underline bug
		myNameInput.setText(myNameInput.getText().toString());
	    }
	});

4) It's ready for use!

Result: When you close the keyboard, the cursor and pointer to your location in the EditText will not show unless you tap on it again.
