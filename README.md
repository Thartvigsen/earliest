# EARLIEST
Source code for "Adaptively-Halting Policy Network for Early Classification", published at KDD'19.
Will be updated prior to KDD'19 conference.

**Update**: The available code is just the model right now, I am currently putting together a full training example with a detailed description of all pieces of the optimization process.

Current use:
```python
from model import EARLIEST

# --- hyperparameters ---
N_FEATURES = 5 # Number of variables in your data (if we have clinical time series recording both heart rate and blood pressure, this would be a 2-dimensional time series, regardless of the number of timesteps)
N_CLASSES = 3 # Number of classes
HIDDEN_DIM = 50 # Hidden dimension of the RNN
CELL_TYPE = "LSTM" # Use an LSTM as the Recurrent Memory Cell.

# --- defining data and model ---
d = torch.rand((5, 1, N_FEATURES)) # A simple synthetic time series.
labels = torch.tensor([0], dtype=torch.long) # A simple synthetic label.
m = EARLIEST(N_FEATURES, N_CLASSES, HIDDEN_DIM, CELL_TYPE) # Initializing the model

# --- inference ---
# Now we can use m for inference
y_hat = m(d)

# --- computing loss and gradients ---
# Computing the loss is quite simple:
loss = m.applyLoss(y_hat, labels)
loss.backward() # Compute all gradients
```
