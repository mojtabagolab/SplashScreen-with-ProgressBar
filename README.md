# SplashScreen-with-ProgressBar
create splash screen Activity with progressbar at the start of program

### pay attention !!
  This tutorial does not include splash screen design (xml code)
  
  ## java class splash screen activity sourse code as follows:
  ```java
  package mojtabagolab.com.splashactivitywithprogressbar;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.os.Handler;
import android.view.View;
import android.widget.ProgressBar;

public class SplashActivity extends AppCompatActivity {

    private ProgressBar prg;

    Handler handler;

    int counter = 0;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_splash);

        prg = findViewById(R.id.progressBar);

        handler = new Handler();

        new Thread(new Runnable() {
            @Override
            public void run() {

                while (counter != 100) {
                    counter += 1;

                    handler.post(new Runnable() {
                        @Override
                        public void run() {
                            prg.setProgress(counter);

                            if (counter == 100) {
                                Intent intent = new Intent(SplashActivity.this, MainActivity.class);
                                startActivity(intent);
                                finish();
                            }
                        }
                    });

                    try {
                        Thread.sleep(25);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
            }
        }).start();
    }
}
```

## the final image of the program performance is as follows:  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
<img src="https://bayanbox.ir/view/567845713627656600/bandicam-2021-10-29-17-35-09-233.gif" />
