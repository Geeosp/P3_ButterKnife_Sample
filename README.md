# Programação 3 - Butter Knife Tutorial

### Tutorial criado para a disciplina Programação 3 (CIn-UFPE) sobre uso do Butter Knife.

O Butter Knife é uma API que busca simplificar a inicialização e utilização de Views em android. Ela oferece:
-Rápida inicialização para objetos que herdam de View.class


## Página Oficial

A documentação oficial do Butter Knife pode ser obtido nos link:
- [Butter Knife](http://jakewharton.github.io/butterknife/)
- [GitHub](https://github.com/JakeWharton/butterknife)

## Instalação

#### Dependência do Gradle
A instalação do Butter Knife é bem simples, Se você estiver usando o Android Studio, basta ir no arquivo build.gradle  e adicionar a seguine linha:

```groovy
compile 'com.jakewharton:butterknife:7.0.1'
```


## Utilização

O uso é bem simples. Se você quiser começar a utilizar o Butter Knife, Não é necessário alterar nada em seu xml de layout. Em nosso tutorial, utilizaremos o seguinte exemplo:

```xml
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    tools:context=".MainActivity">

    <LinearLayout
        android:id="@+id/linearLayout"
        android:layout_width="match_parent"
        android:layout_height="match_parent"

        android:gravity="center"
        android:orientation="vertical">

        EditText
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/edit_text"/>

        extView
            android:layout_width="match_parent"
            android:layout_height="50dp"
            android:id="@+id/text_view"/>

        <View
            android:layout_width="match_parent"
            android:layout_height="300dp"
            android:background="@color/secondary_text_default_material_light"
            android:id="@+id/view">

        </View>

        <SeekBar
            android:id="@+id/seekBarRed"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_above="@+id/linearLayout"
            android:layout_alignParentEnd="true"
            android:layout_alignParentLeft="true"
            android:layout_alignParentRight="true"
            android:layout_alignParentStart="true" />
        <SeekBar
            android:id="@+id/seekBarGreen"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_above="@+id/linearLayout"
            android:layout_alignParentEnd="true"
            android:layout_alignParentLeft="true"
            android:layout_alignParentRight="true"
            android:layout_alignParentStart="true" />
        <SeekBar
            android:id="@+id/seekBarBlue"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_above="@+id/linearLayout"
            android:layout_alignParentEnd="true"
            android:layout_alignParentLeft="true"
            android:layout_alignParentRight="true"
            android:layout_alignParentStart="true" />
       </LinearLayout>

</FrameLayout>

```

O ButterKnife facilita o bind entre views declaradas  no xml de layout e seus objetos respectivos no codigo.
```java
.
.
.
    SeekBar seekBarr;
    SeekBar seekBarg;
    SeekBar seekBarb;
    View view;
    int r=0,g=0,b=0;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
       

        seekBarr = (SeekBar)findViewById(R.id.seekBarRed);
        seekBarb = (SeekBar)findViewById(R.id.seekBarBlue);
        seekBarg = (SeekBar)findViewById(R.id.seekBarGreen);
        view = findViewById(R.id.view);
.
.
.

```
pode ser substituído por:
```java
.
.
.
 @Bind(R.id.seekBarRed)SeekBar seekBarr;
    @Bind(R.id.seekBarGreen)SeekBar seekBarg;
    @Bind(R.id.seekBarBlue)SeekBar seekBarb;
    @Bind(R.id.view)View view;
    int r=0,g=0,b=0;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        ///Logo após o setContentView
        ButterKnife.bind(this);
.
.
.
```
Todas as chamadas de ```findViewById()``` podem ser substituídas por ```ButterKnike.bind(this)```
Lembrando que, para funcionar normalmente, o bind deve ser chamado em algum momento depois do ```setContentView()```
e antes de qualquer View tentar ser utilizada.
