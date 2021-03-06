## ফাংশন  

আমাদের প্রোগ্রামের যে অংশগুলো বার বার আসে সেগুলোকে আমরা পুনরায় ব্যবহারযোগ্য একক (reusable unit) হিসেবে ব্যবহার করতে পারি ফাংশনের সাহায্যে । গনিতে যেমন দেখেছি কোন ফাংশন একটি ইনপুট নিয়ে সেটার উপর বিভিন্ন ধরনের ম্যাথ করে আউটপুট দেয়, প্রোগ্রামিংএও সেই একই ব্যাপার ঘটে । আপনি এক বা একাধিক প্যারামিটার পাস করবেন একটি ফাংশনে, ফাংশনটি প্রসেস করে আপনাকে আউটপুট “রিটার্ন করবে” । তবে প্রোগ্রামিং এর ক্ষেত্রে সবসময় যে ইনপুট থাকতে হবে বা আউটপুট দিতে হবে এমন কোন কথা নেই ।

একটি ফাংশন আসলে কিছু স্টেটমেন্টের সংকলন । যখনই কোন ফাংশন কল করা হয় তখন এই ফাংশনের ভিতরে থাকা স্টেটমেন্টগুলো এক্সিকিউট করা হয় । পাইথনে আমরা ফাংশন ডিক্লেয়ার করার জন্য def কি-ওয়ার্ডটি ব্যবহার করি । আসুন দেখে নেই একটি ফাংশন:

```python
def hello():
    print("Hello World!")
```

প্রথমে আমরা `def` কি-ওয়ার্ডটি লিখেছি । তারপর ফাংশনের একটা নাম দিয়েছি – `hello`, এবং তারপর একজোড়া প্রথম বন্ধনী `()`. এরপর একটি কোলন তথা `:` চিহ্ন দিয়ে এর নিচে ফাংশনের আওতাভুক্ত কোড ব্লক বা ফাংশনের কাজ ডিফাইন (নির্ধারণ) করেছি। ফাংশনটির কাজ হচ্ছে “Hello world!” বাক্যটি প্রিন্ট করা।   

কিন্তু এভাবে একটা ফাংশনকে প্রোগ্রামের মধ্যে শুধু ডিফাইন করে রেখে দিলে তার মধ্যের কোড বা ইন্সট্রাকশন গুলো এমনি এমনি কাজ করবে না। এর জন্য ওই ফাংশনটিকে তার নাম ধরে কল করতে হবে। কল কিভাবে করতে হয়? কিছুই না ওই ফাংশনের নামটি সাধারণ ভাবে স্টেটমেন্ট আকারে লিখলেই হয়। যেমন - আমরা `print` ফাংশন ব্যবহার করি যখন দরকার হয় তখন। উপরের ফাংশনটিকে কল করতে হবে নিচের মত করে,  

```python
hello()
```   

তাই পুরো প্রোগ্রামটি যদি নিচের মত হয়, 

```python
# Defining the function named hello
def hello():
    print("Hello World!")
    
# Calling the function to use it
hello()    
```


তাহলে এই প্রোগ্রামটির আউটপুট হবে, 

```python
Hello World!
```  

একটা ফাংশনকে প্রোগ্রামে একবার ডিফাইন করলেও সেটাকে বার বার কল বা ব্যবহার করা যাবে। অর্থাৎ নিচের মত - 

```python
# Defining the function named hello
def hello():
    print("Hello World!")
    
# Calling the function to use it
hello()    

# Again calling the function
hello()    
```

আউটপুট,

```python
Hello World!
Hello World!
```  


একটি কথা মনে রাখা জরুরি। কোন ফাংশনকে কল করার বা ব্যবহার করার আগেই সেই ফাংশনকে প্রোগ্রামে ডিফাইন বা প্রোগ্রামের কাছে চিহ্নিত করতে হবে। যেমন - উপরের প্রোগ্রামটিকে যদি আমরা নিচের মত করে লিখি, 

```python
# Calling the function to use it
hello()

# Defining the function named hello
def hello():
    print("Hello World!")
```   

তাহলে আউটপুট আসবে,  

```python
NameError: name 'hello' is not defined
```   

এটা সহজ ভাবে চিন্তা করলেই যৌক্তিক মনে হবে। অর্থাৎ, যদি প্রোগ্রামের শুরুতেই একটি ফাংশনকে কল বা ব্যবহার করতে চাই, তাহলে কিভাবে আমার প্রোগ্রাম জানবে যে তার মধ্যে `hello` নামের একটা ফাংশন আছে? বরং এটাই কি যৌক্তিক নয় যে - আগে ফাংশনটাকে প্রোগ্রামে ডিফাইন করবো এবং তার পর প্রোগ্রামের কোন এক বা একাধিক যায়গায় সেটাকে কল করবো।?   

কাস্টম ফাংশনকে অনেকটা আপনার দ্বারা তৈরি একটা ছোট্ট মেশিনের সাথে তুলনা করা যায়। অর্থাৎ একবার মেশিনটি তৈরি করবো আর বার বার ব্যবহার করে কিছু একটা কাজ করব বা জিনিষ তৈরি করবো। কিছু তৈরি করতে হলে মেশিনে কিছু ইনপুট দিতে হতে পারে। আবার কিভাবে তৈরি করবে সেটাও মেশিনের মধ্যে যন্ত্রপাতি বসিয়ে সেটআপ করতে হবে। এভাবে বাস্তবে একটা মেশিন তৈরি করাকেই প্রোগ্রামের মধ্যে ফাংশন ডিফাইন করা বলা যেতে পারে।  

