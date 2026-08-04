# Gemini Vertex describes an image

[🇯🇵 日本語](README.md) | [🇺🇸 English](README.en.md)

## 1. Business Logic Flow

		User
		 │
		 │ 1. Ask a question
		 │
		 ▼
		Application
		 │
		 │ 2. Receive prompt
		 │
		 │ 3. Receive image
		 │
		 ▼
	Prepare AI Request
		 │
		 │ Build request:
		 │   - Prompt
		 │   - Image
		 │   - Model
		 │
		 ▼
	Vertex AI
		 │
		 │ Analyze image
		 │
		 │ Understand prompt
		 │
		 │ Generate answer
		 │
		 ▼
	Application
		 │
		 │ Receive response
		 │
		 │ Extract text
		 │
		 ▼
		User


## 2. Create the Client

```
client, err := genai.NewClient(ctx, projectID, location)

```
This does not call Gemini. Instead, it creates a client object.
Internally, it roughly does this:

Application
      │
      ▼
Read Credentials
      │
      ▼
Initialize HTTP Client
      │
      ▼
Store Project ID
      │
      ▼
Store Region
      │
      ▼
Return Client

## 3. Get the Model

```
model := client.GenerativeModel(modelName)

```

## 4. Prepare the Image

```
img := genai.FileData{
    MIMEType: "image/jpeg",
    FileURI: image,
}
```

## 5. Prepare the Prompt

```
genai.Text(prompt)
```


## 6. GenerateContent()

```
res, err := model.GenerateContent(
    ctx,
    img,
    genai.Text(prompt),
)
```

We see the image 
<img src="sample.png" widh="100%" />



