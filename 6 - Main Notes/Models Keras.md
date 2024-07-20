2024-07-21 - 00:22
Status:
Tags: [[sequential]] [[functional]] [[keras]]
# Models Keras

In Keras, the Sequential and Functional APIs provide two different ways to build neural network models. Here's a breakdown of the differences between them:

## Sequential API

1. **Simplicity**:
   - The Sequential API is straightforward and easy to use.
   - You stack layers one after the other in a linear fashion.

2. **Usage**:
   - Best suited for simple, single-input, single-output stacks of layers.
   - Works well for beginners or for quick prototyping.

3. **Syntax**:
   ```python
   from keras.models import Sequential
   from keras.layers import Dense

   model = Sequential()
   model.add(Dense(64, activation='relu', input_shape=(784,)))
   model.add(Dense(64, activation='relu'))
   model.add(Dense(10, activation='softmax'))
   ```

4. **Limitations**:
   - Cannot create models with multiple inputs or outputs.
   - Cannot create complex models such as those with shared layers, non-linear topology, or models that reuse layers.

## Functional API

1. **Flexibility**:
   - The Functional API is more flexible and powerful.
   - Allows for the creation of complex models including multi-input, multi-output models, shared layers, and models with residual connections.

2. **Usage**:
   - Suitable for more complex architectures where you need more control over the network structure.
   - Can be used to create models that are beyond the capabilities of the Sequential API.

3. **Syntax**:
   ```python
   from keras.models import Model
   from keras.layers import Input, Dense

   inputs = Input(shape=(784,))
   x = Dense(64, activation='relu')(inputs)
   x = Dense(64, activation='relu')(x)
   outputs = Dense(10, activation='softmax')(x)

   model = Model(inputs=inputs, outputs=outputs)
   ```

4. **Advantages**:
   - Enables the creation of more sophisticated models.
   - Allows for more detailed model visualization and understanding.

## Summary

- **Sequential API**: Simple and linear, suitable for basic models.
- **Functional API**: Flexible and powerful, suitable for complex models with multiple inputs/outputs, shared layers, and more intricate architectures.

Choosing between the two depends on the complexity and requirements of the model you wish to build. For straightforward tasks, the Sequential API is often sufficient. For more advanced tasks, the Functional API provides the necessary tools to construct and manage intricate model architectures.

# Reference