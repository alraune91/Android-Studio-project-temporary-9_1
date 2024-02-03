![window1](https://github.com/alraune91/Android-Studio-project-temporary-9_1/blob/main/Screenshot_7.png)

PROGRAME CODE:
import androidx.appcompat.app.AppCompatActivity;

import android.annotation.SuppressLint;
import android.content.Intent;
import android.graphics.Color;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.CheckBox;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity implements View.OnClickListener{
    public float resultBMI;
    private EditText etAge;
    private EditText etHigth;
    private EditText etWeigth;
    private Button btnCal;
    private CheckBox lMale;
    private CheckBox lFemale;

    @SuppressLint("MissingInflatedId")
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        etAge = findViewById(R.id.etY);
        etHigth = findViewById(R.id.etCM);
        etWeigth = findViewById(R.id.etKG);
        btnCal = findViewById(R.id.btnShow);
        lMale =  findViewById(R.id.chbW);
        lFemale = findViewById(R.id.chbM);
        btnCal.setOnClickListener(this);
        lMale.setOnClickListener(this);
        lFemale.setOnClickListener(this);
    }
    public void onClick(View v){
        int id = v.getId();
        if (id == R.id.btnShow) {
            int weigth = Integer.parseInt(etWeigth.getText().toString());
            int age = Integer.parseInt(etAge.getText().toString());
            int higth = Integer.parseInt(etHigth.getText().toString());
            resultBMI = weigth / ((higth / 100f) * (higth / 100f));
            Intent intent = new Intent();
            intent.setClass(MainActivity.this, ResultsActivity.class);
            intent.putExtra("res", resultBMI);
            intent.putExtra("age", age);
            startActivity(intent);
        } else if (id == R.id.chbW) {
            lMale.setBackgroundColor(Color.RED);
            lFemale.setBackgroundColor(Color.TRANSPARENT);
        } else if (id == R.id.chbM) {
            lMale.setBackgroundColor(Color.TRANSPARENT);
            lFemale.setBackgroundColor(Color.BLUE);
        }
    }
    public  void Exit()
    {
        finish();
    }
}
